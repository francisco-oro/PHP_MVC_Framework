# PHP MVC Framework - By Francisco Oro 🏑

## Models

## Views

## Controllers

## Routing
You can specify the `controller` as the first url segment and the `action` as the second one
### Routing table
When the framework receives a request, it matches the url path to the list of routes to determine which controller or
action to run. 

| Route       | Controller | Action |
|-------------|:----------:|-------:|
| "/"         |    Home    |  index |
| "/products" |  Products  |  index |
| "/show/123" |  Products  |   show |

The `Router` class gets the job done for us. You need to pass the `path` as the first parameter and the `controller` object
which is an associative array with the keys `controller` and `action` as the second one. 

```php
$router = new Router();

$router->add("/home/index", ["controller" => "home", "action" => "index"]);
$router->add("/products", ["controller" => "products", "action" => "index"]);
$router->add("/", ["controller" => "home", "action" => "index"]);
```

Then, retrieve the `action` and `controller` respectively from the `match` method
```php
$path = parse_url($_SERVER["REQUEST_URI"], PHP_URL_PATH);
...

$params  = $router->match($path);

$action = $params["action"];
$controller = $params["controller"];
```