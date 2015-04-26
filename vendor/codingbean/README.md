Letphp
=====

Letphp is a simple, open source PHP router. It's super small (~150 LOC), fast, and sexy. This class allows you to jus throw it into your project and start using it immediately.

### Install

If you have Composer, just include Letphp as a project dependency in your `composer.json`. If you don't just install it by downloading the .ZIP file and extracting it to your project directory.

```
require: {
    "noahbuscher/letphp": "master"
}

```

### Examples

First, `use` the Letphp namespace:

```PHP
use \NoahBuscher\Letphp\Letphp;
```

Letphp is not an object, so you can just make direct operations to the class. Here's the Hello World:

```PHP
Letphp::get('/', function() {
  echo 'Hello world!';
});

Letphp::dispatch();
```

Letphp also supports lambda URIs, such as:

```PHP
Letphp::get('/(:any)', function($slug) {
  echo 'The slug is: ' . $slug;
});

Letphp::dispatch();
```

You can also make requests for HTTP methods in Letphp, so you could also do:

```PHP
Letphp::get('/', function() {
  echo 'I <3 GET commands!';
});

Letphp::post('/', function() {
  echo 'I <3 POST commands!';
});

Letphp::dispatch();
```

Lastly, if there is no route defined for a certain location, you can make Letphp run a custom callback, like:

```PHP
Letphp::error(function() {
  echo '404 :: Not Found';
});
```

If you don't specify an error callback, Letphp will just echo `404`.

<hr>

In order to let the server know the URI does not point to a real file, you need to use the included [.htaccess](http://httpd.apache.org/docs/2.2/howto/htaccess.html) file.
