# RSSClient

[![Build Status](https://secure.travis-ci.org/desarrolla2/RSSClient.png)](http://travis-ci.org/desarrolla2/RSSClient)
##
RSSClient is a simple to use RSS library to fetch and use RSS feeds.
RSSClient is very fast!

You can read the RSS specification on [RFC](http://cyber.law.harvard.edu/rss/rss.html)

RSSClient Support Atom1.0 now.


## Installation

### With Composer

It is best installed it through [packagist](http://packagist.org/packages/desarrolla2/rss-client) 
by including
`desarrolla2/rss-client` in your project composer.json require:

``` json
    "require": {
        // ...
        "desarrolla2/rss-client":  "dev-master"
    }
```

### Without Composer

You can also download it from [Github] (https://github.com/desarrolla2/RSSClient), 
but no autoloader is provided so you'll need to register it with your own PSR-0 
compatible autoloader.

## Usage

### Without Cache

This example does not use any cache, so it probably will be too slow to be used on 
a website, you should implement your system cache, or use the cache system described below

``` php
    <?php

    use Desarrolla2\RSSClient\RSSClient;

    $client = new RSSClient();

    $client->addFeeds(array(
            'http://news.ycombinator.com/rss',
            'http://feeds.feedburner.com/TechCrunch/',
                ), 'news'
        );

    $feeds = $client->fetch('news');

```

### With Cache

This example uses the cache implemented by Seller desarrolla2/cache you must 
select the adapter depending on your needs, you can find all the info in the 
repository [Github] (https://github.com/desarrolla2/Cache).

``` php
    <?php

    use Desarrolla2\RSSClient\Cache\RSSClient;
    use Desarrolla2\Cache\Cache;
    use Desarrolla2\Cache\Adapter\File;

    // It is important that you select and configure your cache adapter
    $client = new RSSClient());
    $client->setCache(new Cache(new File('/tmp')));

```

You can see how to configure desarrolla2/cache in its [README] (https://github.com/desarrolla2/Cache)

The rest of the procedure is exactly the same as if you were using the client without cache.

``` php
    <?php
    
    $client->addFeeds(array(
        'http://news.ycombinator.com/rss',
        'http://feeds.feedburner.com/TechCrunch/',
        ), 'news'
    ));

    $feeds = $client->fetch('news');

```

## Formats

* RSS20
* Atom10

## Code Coverage

Do you want to see RSSClient Code Coverage see [here](http://rssclient.desarrolla2.com/coverage/index.html)

## Contact

You can contact with me on [twitter](https://twitter.com/desarrolla2).
