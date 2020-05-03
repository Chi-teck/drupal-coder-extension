# Extended Drupal Coding Standard
This project offers a set of preconfigured rules for PHP Code Sniffer mainly related to new PHP features that are not
covered by Drupal coding standards yet.
 
## System Requirements
PHP 7.3+

## Installation
Install the standard locally through Composer. 
```
composer require --dev chi-teck/drupal-coder-extension
```
Add "DrupalExtended" standard to your project's phpcs.xml.
The actual name of the standard depends on PHP version you use. For instance, the name
"DrupalExtended73" corresponds to PHP 7.3+ projects.

```xml
<?xml version="1.0"?>
<ruleset name="My Project">
  <rule ref="vendor/chi-teck/drupal-coder-extension/DrupalExtended73">
    <!-- Sniffs to exclude. -->
  </rule>
</ruleset>
```
A complete example of `phpcs` configuration for Drupal 8+ sites powered by PHP 7.4+.
```xml
<?xml version="1.0"?>
<ruleset name="My Project">
  <description>PHP Code Sniffer configuration for My Project.</description>
  <arg name="colors"/>
  <arg name="extensions" value="php,module,inc,install,theme,info,txt,md,yml"/>
  <file>./docroot/modules/custom</file>
  <file>./docroot/themes/custom</file>
  <file>./tests</file>
  <!-- Exclude vendors. -->
  <exclude-pattern>./docroot/themes/custom/example/node_modules</exclude-pattern>
  <rule ref="vendor/drupal/coder/coder_sniffer/Drupal">
    <!-- Exclude in favor of native typehints. -->
    <exclude name="Drupal.Commenting.VariableComment.MissingVar"/>
  </rule>
  <rule ref="vendor/drupal/coder/coder_sniffer/DrupalPractice"/>
  <rule ref="vendor/chi-teck/drupal-coder-extension/DrupalExtended74"/>
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

## Links
* [PHP Code Sniffer](https://github.com/squizlabs/PHP_CodeSniffer)
* [Drupal Coding Standards](https://www.drupal.org/node/2802991)
* [Drupal Coder](https://www.drupal.org/project/coder)
* [Slevomat Coding Standard](https://github.com/slevomat/coding-standard)

## License
GNU General Public License, version 2 or later.
