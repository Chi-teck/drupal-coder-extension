# Extended Drupal Coding Standard

A highly opinionated extension for Drupal Coding Standards.

## Installation

Install the standard locally through Composer. 
```
composer require --dev chi-teck/drupal-coder-extension
```

Add "DrupalExtended" standard to your project's ruleset.xml along with other Drupal Coding Standards.
The actual name of the standard depends on PHP version you use.

```xml
<?xml version="1.0"?>
<ruleset name="MyProject">
  <rule ref="vendor/drupal/coder/coder_sniffer/Drupal"/>
  <rule ref="vendor/drupal/coder/coder_sniffer/DrupalPractice"/>
  <rule ref="vendor/chi-teck/drupal-coder-extension/DrupalExtended73/ruleset.xml">
    <!-- Sniffs to exclude. -->
  </rule>
</ruleset>
```

## Links
* [PHP Code Sniffer](https://github.com/squizlabs/PHP_CodeSniffer)
* [Drupal Coding Standards](https://www.drupal.org/node/2802991)
* [Drupal Coder](https://www.drupal.org/project/coder)
* [Slevomat Coding Standard](https://github.com/slevomat/coding-standard)

## License
GNU General Public License, version 2 or later.
