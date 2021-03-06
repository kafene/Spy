#Spy

Spy is a simple dependency injection container. It gets its flexibility
by having dependency injections declared as callables, usually Closures.

##Usage:

```
$container = new \Spy\Container;
$container->set('http_client', function() {
	return new \Zend\Http\Client;
});

$instanceOfHTTPClient = $container->get('http_client');
```

You can also pass arguments to your callable in the `get` call,
as such:

```
$container->set('foo_bar', function($foo, $bar) {
	return new FooBar($foo, $bar);
});

$instanceOfFooBar = $container->get('foo_bar', 'hello', 'world');
```

You can check if a dependency injection exists by its name with the
`has` method:

```
print $container->has('yaml_parser'); // bool
```

You can remove a dependency injection with the `remove` method:

```
$container->remove('markdown_parser');
```
