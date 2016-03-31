[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/GFG/dto-url/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/GFG/dto-url/?branch=master)
[![Code Coverage](https://scrutinizer-ci.com/g/GFG/dto-url/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/GFG/dto-url/?branch=master)
[![Build Status](https://scrutinizer-ci.com/g/GFG/dto-url/badges/build.png?b=master)](https://scrutinizer-ci.com/g/GFG/dto-url/?branch=master)
[![Latest Stable Version](https://poser.pugx.org/gfg/dto-url/v/stable)](https://packagist.org/packages/gfg/dto-url)
[![Total Downloads](https://poser.pugx.org/gfg/dto-url/downloads)](https://packagist.org/packages/gfg/dto-url)
[![License](https://img.shields.io/badge/license-GPLv3-blue.svg)]()
[![Forks](https://img.shields.io/github/forks/GFG/dto-url.svg)]()
[![Stars](https://img.shields.io/github/stars/GFG/dto-url.svg)]()


INTRODUCTION
============

Tiny library for encapsulating an URL.

EXAMPLES OF USE
===============

```php
<?php

use GFG\DTOUrl\Url;

$urlParts = [
    'scheme'   => 'http',
    'host'     => 'externalshop.com',
    'port'     => 80,
    'user'     => 'username',
    'pass'     => 'password',
    'path'     => ['api', 'version', 'action'],
    'query'    => ['query' => 'string'],
    'fragment' => 'first'
];
$url = new Url($urlParts);

// http://username:password@externalshop.com:80/api/version/action?query=string#first
echo $url->getFullUrl();
```

```php
<?php

use GFG\DTOUrl\Url;

$urlParts = [
    'scheme'   => 'https',
    'host'     => 'www.externalshop.com',
    'path'     => ['test']
];
$url = new Url($urlParts);

// https://www.externalshop.com/test
echo $url->getFullUrl();
```

```php
<?php

use GFG\DTOUrl\Url;

$urlParts = [
    'path' => [
        'api', 
        'version' => 'version',
        'partnerCode' => 'partner-code',
        'product'
    ]
];
$url = new Url($urlParts);

$replace = [
    'version'     => 2,
    'partnerCode' => 'kanui'
];
$url->replacePath($replace);

// api/2/kanui/product
echo $url->getFullUrl();
```

```php
<?php

use GFG\DTOUrl\Url;

$urlParts = [
    'scheme'   => 'http',
    'host'     => 'externalshop.com',
    'port'     => 80,
    'user'     => 'username',
    'pass'     => 'password',
    'path'     => ['api', 'version', 'action'],
    'query'    => ['query' => 'string'],
    'fragment' => 'first'
];
$url = new Url($urlParts);

$paths = [
    'version' => 'version',
    'create',
    'product'
];
$replace = ['version' => '2.0'];
$url->setPath($paths)->replacePath($replace);

// http://username:password@externalshop.com:80/2.0/create/product?query=string#first
echo $this->url->getFullUrl();
```

```php
<?php

use GFG\DTOUrl\Url;

$urlParts = [
    'scheme'   => 'http',
    'host'     => 'externalshop.com',
    'port'     => 80,
    'user'     => 'username',
    'pass'     => 'password',
    'path'     => ['api', 'version', 'action'],
    'query'    => ['query' => 'string'],
    'fragment' => 'first'
];
$url = new Url($urlParts);

$query = ['name' => 'name'];
$replace = ['name' => 'fullname'];
$url->setQuery($query)->replaceQuery($replace);

// http://username:password@externalshop.com:80/api/version/action?name=fullname#first
echo $url->getFullUrl();
```
