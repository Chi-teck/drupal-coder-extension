# Extended Drupal Coding Standard

This project offers a set of preconfigured rules for PHP Code Sniffer mainly related to new PHP features that are not
covered by Drupal coding standards yet.
 
## System Requirements

PHP 8.1+

## Installation

Install the standard locally through Composer. 

```shell
composer require --dev chi-teck/drupal-coder-extension
```

Add `DrupalExtended` standard to your project's `phpcs.xml`.

```xml
<?xml version="1.0"?>
<ruleset name="Drupal Extended"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:noNamespaceSchemaLocation="../vendor/squizlabs/php_codesniffer/phpcs.xsd">
  <rule ref="vendor/chi-teck/drupal-coder-extension/DrupalExtended">
    <!-- Sniffs to exclude. -->
  </rule>
    
  <!-- Override settings for enabled rules or enable that excluded. -->
  <rule ref="SlevomatCodingStandard.Classes.RequireAbstractOrFinal.ClassNeitherAbstractNorFinal">
      <exclude-pattern>./src/Exception</exclude-pattern>
  </rule>
  <rule ref="SlevomatCodingStandard.ControlStructures.EarlyExit"/>
</ruleset>
```

A complete example of `phpcs.xml`:

```xml
<?xml version="1.0"?>
<ruleset name="Drupal Extended"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:noNamespaceSchemaLocation="../vendor/squizlabs/php_codesniffer/phpcs.xsd">
  <description>PHP Code Sniffer configuration for My Project.</description>
  <arg name="colors"/>
  <arg name="extensions" value="php,module,inc,install,theme,info,txt,md,yml"/>
    
  <!-- Paths to scan for problems recursively. -->
  <file>./web/modules/custom</file>
  <file>./web/themes/custom</file>
  <file>./tests</file>

  <!-- Exclude vendors. -->
  <exclude-pattern>./docroot/themes/custom/example/node_modules</exclude-pattern>

  <rule ref="vendor/chi-teck/drupal-coder-extension/DrupalExtended"/>
</ruleset>
```

## Usage

Run the `phpcs` script to check custom code.

```
./vendor/bin/phpcs -ps --standard=phpcs.xml
```

Run the `phpcbf` script to automatically correct coding standard violations.

```
./vendor/bin/phpcbf
```

You also can put this command into projects `composer.json`:

```json
{
  …
  "scripts": {
    "phpcs": "vendor/bin/phpcs -ps"
  }
}
```

Then you can use it like

```shell
composer phpcs
```

## Links

* [PHP Code Sniffer](https://github.com/squizlabs/PHP_CodeSniffer)
* [Drupal Coding Standards](https://www.drupal.org/node/2802991)
* [Drupal Coder](https://www.drupal.org/project/coder)
* [Slevomat Coding Standard](https://github.com/slevomat/coding-standard)

## License

GNU General Public License, version 2 or later.
