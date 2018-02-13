# Mailgun PHP light

A light and minimalistic PHP client library for sending mails using Mailgun API with no external dependencies.
This library was created to provide a very simple curl abstraction for sending mails using the Mailgun HTTP API.
This is an alternative to those who need to just send simple mails and think the original PHP Client is to heavy for them and have a to much dependencies.

## Installation

```bash
composer require 'eldadfux/mailgun-light:1.0.1'
```

## Example

```php
$apiKey    = 'your-api-key-here';
$apiDomain = 'your-api-sending-domain-here';

$mailgun = new \MailgunLight\MailgunLight($apiKey, $apiDomain);

$mailgun
    ->setFrom('team@example.com', 'Team Example')
    ->setReplyTo('this@gmail.com') // optional
    ->addRecipient('user1@example.com', 'User 1 Name')
    ->addRecipient('user2@example.com', 'User 2 Name')
    ->addRecipient('user3@example.com', 'User 3 Name')
    ->setSubject('Hello World')
    ->setText('I am a string')
    ->setHTML('<b>I am a string</b>')
;

// Send Mail
if(!$mailgun->send()) {
    throw new Exception('Problem sending mail: ' . $mailgun->getError());
}

// Subscribe to newsletter
$mailgun->subscribe('newsletter@example.com', 'user1@example.com');

```

## Contributing

All code contributions - including those of people having commit access - must go through a pull request and approved by a core developer before being merged. This is to ensure proper review of all the code.

Fork the project, create a feature branch, and send us a pull request.


### Versioning

For transparency and insight into our release cycle, and for striving to maintain backward compatibility, This project will be maintained under the Semantic Versioning guidelines as much as possible. Releases will be numbered with the following format:

`<major>.<minor>.<patch>`

For more information on SemVer, please visit [http://semver.org/](http://semver.org/).


## Requirements

PHP 7+

We recommend using the latest PHP version whenever possible.

## Author

**Eldad A. Fux**

+ [https://twitter.com/eldadfux](https://twitter.com/eldadfux)
+ [https://github.com/eldadfux](https://github.com/eldadfux)

## License

This project is licensed under the MIT License - see the LICENSE file for details
