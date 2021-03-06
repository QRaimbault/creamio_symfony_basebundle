# CreamIO Symfony Base Bundle

This bundle is a base for the CreamIO 
symfony bundles over [Symfony 4.0][3].

Requirements
------------

  * Symfony 4;
  * PHP 7.2 or higher;
  * Composer;
  * MySQL database;
  * PDO PHP extension;
  * and the [usual Symfony application 
requirements][1].
  
Installation
------------

Require the bundle from a symfony 4 application.

You must configure the logger channel to log to database by modifying `config/packages/(dev|prod)/monolog.yaml` this way :
```yaml
    channels: ['db']
    handlers:
        db:
            channels: ['db']
            type: service
            id: cream_io_base.loggingservice
```

You MUST NOT modify anything in this configuration, as the services are injected in the bundle for logger providing.

Usage
-----

Autowire or inject `CreamIO\BaseBundle\Service\LoggerProvider` in your service/controller.  
You can then log this way : 
```php
$logger = $loggerProvider->logger();
$logger->info('My information to log', ['userId', $user->getId()]);    
```

The second parameter is the context, it can be an array of whatever you want to identify the logging context.

Project tree
------------

```bash
.
└── src
    ├── DependencyInjection
    ├── EventSubscriber     # Exception event subscriber
    ├── Exceptions          # APIError and APIException for error handling in API
    ├── Resources
    │   └── config          # Service injection
    └── Service             # API Service handling JSON responses
```

License
-------
[![Creative Commons License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png)](http://creativecommons.org/licenses/by-nc-sa/4.0/)

This software is distributed under the terms of the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International Public License. License is described below, you can find a human-readable summary of (and not a substitute for) the license [here](http://creativecommons.org/licenses/by-nc-sa/4.0/).

[1]: 
https://symfony.com/doc/current/reference/requirements.html
[2]: 
https://symfony.com/doc/current/cookbook/configuration/web_server_configuration.html
[3]: https://symfony.com/
