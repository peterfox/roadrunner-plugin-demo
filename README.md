# RoadRunner Plugin Template

<p align="center">
 <a href="https://github.com/peterfox/roadrunner-plugin-demo/releases"><img src="https://img.shields.io/github/v/release/peterfox/roadrunner-plugin-demo.svg?maxAge=30"></a>
	<a href="https://pkg.go.dev/github.com/peterfox/roadrunner-plugin-demo"><img src="https://godoc.org/github.com/peterfox/roadrunner-plugin-demo?status.svg"></a>
	<a href="https://github.com/peterfox/roadrunner-plugin-template/actions"><img src="https://github.com/peterfox/roadrunner-plugin-demo/workflows/tests/badge.svg"></a>
	<a href="https://goreportcard.com/report/github.com/peterfox/roadrunner-plugin-demo"><img src="https://goreportcard.com/badge/github.com/peterfox/roadrunner-plugin-demo"></a>
	<a href="https://lgtm.com/projects/g/peterfox/roadrunner-plugin-demo/alerts/"><img alt="Total alerts" src="https://img.shields.io/lgtm/alerts/g/peterfox/roadrunner-plugin-demo.svg?logo=lgtm&logoWidth=18"/></a>
    <img alt="All releases" src="https://img.shields.io/github/downloads/peterfox/roadrunner-plugin-demo/total">
</p>

## Installation

To use this plugin with RoadRunner you will need to fork or clone your
own copy of the [RoadRunner binary](https://github.com/spiral/roadrunner-binary).

You can import the plugin via go modules:

```sh
go get github.com/peterfox/roadrunner-plugin-demo
```

From there you can edit the [plugins.go](https://github.com/spiral/roadrunner-binary/blob/stable/internal/container/plugins.go) file to
import the plugin.

```go
package container

import (
    // ...
    demoPlugin "github.com/peterfox/roadrunner-plugin-demo"
    // ...
)

// Plugins returns active plugins for the endure container. Feel free to add or remove any plugins.
func Plugins() []interface{} {
	return []interface{}{
        // ...
        &demoPlugin.Plugin{},
        // ...
    }
}

```

By importing this plugin and registering it the plugin will be compiled into the final binary.

The plugin will require that the _.rr.yaml_ config has the key `plugin` for the plugin won't initialise with roadrunner.

```yaml
plugin:
  value: foobar
```

## Usage

To make use of this plugin via PHP you must install the [Spiral Goridge](https://github.com/spiral/goridge-php) library.

You can use the following code as an example in php:

```php
<?php

use Spiral\Goridge\RPC\RPC;
use Spiral\RoadRunner\Environment;

$rpc = RPC::create(Environment::fromGlobals()->getRPCAddress());

// returns ['message' => 'test']
$output = $rpc->call('plugin.Message', ['message' => 'test']);
```

## Testing

You may download the project and test the plugin using the following command.

```bash
go test
```

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Contributing

Please see [CONTRIBUTING](.github/CONTRIBUTING.md) for details.

## Security Vulnerabilities

Please review [our security policy](../../security/policy) on how to report security vulnerabilities.

## Credits

- [Peter Fox](https://github.com/peterfox)
- [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
