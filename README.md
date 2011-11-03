
# PHP oEmbed consumer library

Simple consumer library for [oEmbed](http://oembed.com/).

## Usage

``` php
<?php

use Alb\OEmbed;

$response = OEmbed\Simple::request('http://vimeo.com/31423544', array(
    'maxwidth' => 400,
    'maxheight' => 300,
));

echo $response->getTitle();
echo $response->getHtml();
```

### Advanced usage:

``` php
<?php

use Alb\OEmbed;

// instanciate a Provider from a known endpoint
$provider = new OEmber\Provider('http://vimeo.com/api/oembed.json', 'json');

// request information about a resource
$response = $provider->request('http://vimeo.com/31423544');
```

The library is also capable of dicovering the oEmbed enpoint from a resource URL (if the site supports it):

``` php
<?php

use Alb\OEmbed;

$discovery = new OEmbed\Discovery;
$provider = $disovery->discover('http://vimeo.com/31423544');

// or, using OEmbed\Simple:

$provider = OEmbed\Simple::getProvider('http://vimeo.com/31423544');
```

