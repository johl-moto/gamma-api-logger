# SmartGamma API Logger Bundle

##About

SmartGamma Symfony2 REST API Logger bundle is a tool that used to create [SmartGamma Symfony2 REST APIs](http://smart-gamma.com/).It enables detailed logging (possible to separate log) for incomming calls for your API and tracks the duration, requests and responses body. As additional feature it allows to profile your APIs and tracks slow API calls.

##Installation

1. Using Composer
To install GammaApiLoggerBundle with Composer just add the following to your composer.json file:

```
// composer.json
{
    // ...
    require: {
        // ...
        "gamma/api-logger-bundle": "dev-master"
    }
}
```

Then, you can install the new dependencies by running Composer’s update command from the directory where your composer.json file is located:

```
php composer.phar update gamma/api-logger-bundle
```

Now, Composer will automatically download all required files, and install them for you. All that is left to do is to update your AppKernel.php file, and register the new bundle:

```php
<?php

// in AppKernel::registerBundles()
$bundles = array(
    // ...
    new Gamma\GammaApiLoggerBundle\GammaApiLoggerBundle(),
    // ...
);
```

##Configuration

By default the bundle is enabled and slow API call limit is 1000ms. To chage these settings either add tp your parameters.yml
```
// parameters.yml
   gamma_logger_enabled: true
   gamma_logger_slow_time_limit: 1000
```  
or add to config.yml
```
// config_dev.yml
parameters:
   gamma_logger_enabled: true
   gamma_logger_slow_time_limit: 500
```

```
// config_prod.yml
parameters:
   gamma_logger_enabled: false
```

##Usage

Once the bundle was enabled, it will start to make logging all requests that have prefix "/api/" in URI to the log as shown on the sample

![logging]

All API calls will be logged with "info" level.
API calls that will take more then "gamma_logger_slow_time_limit" value will be logged with "error" level  

##TODO

1. make hardcoded prefix "/api/" configurable 

[logging]: http://smart-gamma.com/files/2016-07/smart-gamma-logger-api-log.png
