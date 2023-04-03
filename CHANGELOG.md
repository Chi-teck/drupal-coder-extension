# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

- Added `CHANGELOG.md` file.

### Changed

- Update Composer dependencies.

## [2.0.0-alpha2] - 2023-02-24

### Changed

- Excluded `SlevomatCodingStandard.Commenting.RequireOneLineDocComment.MultiLineDocComment`
- Excluded `SlevomatCodingStandard.ControlStructures.JumpStatementsSpacing`
- Excluded `SlevomatCodingStandard.Operators.RequireOnlyStandaloneIncrementAndDecrementOperators`
- `SlevomatCodingStandard.Functions.ArrowFunctionDeclaration` now allows multi-line arrow function.
- Improved README.md with examples how to enable excluded rules or change their settings.

## [2.0.0-alpha1] - 2023-02-23

### Changed

- More checks are enabled by default.
- Changed main logic of the controlling rules. Previously they have been enabled one-by-one on demand, now we exclude the ones that conflict or duplicate Drupal Coder rulesets, or simply very specific, everything else enabled by default.
- Rulesets no more attached to PHP versions. Sniffers are automatically enabled on languages for which they are available. E.g. there will be no checks for promoted properties on PHP 7.4, but will be on 8.0+.
- Drupal's coder rulesets `Drupal` and `DrupalPractice` are now included by default but slightly adjusted to not conflict with other checks. You don't need to include them manually now.

### Migrating from 1.x

1. Require new version
    ```shell
    composer require chi-teck/drupal-coder-extension:^2.0@alpha
    ```
2. In `phpcs.xml` replace `<rule ref="vendor/chi-teck/drupal-coder-extension/DrupalExtended73"/>` and/or `<rule ref="vendor/chi-teck/drupal-coder-extension/DrupalExtended74"/>` by
    ```xml
    <rule ref="vendor/chi-teck/drupal-coder-extension/DrupalExtended"/>
    ```
3. If you have `<rule ref="vendor/drupal/coder/coder_sniffer/Drupal"/> and/or `<rule ref="vendor/drupal/coder/coder_sniffer/DrupalPractice"/>`  without rules overrides — you can remove them, they're now included by default in `DrupalExtended`.
4. If you have rules overrides for `Drupal` sniffers, take a look at [current overrides](https://github.com/Chi-teck/drupal-coder-extension/blob/2.x/DrupalExtended/ruleset.xml#L5-L16) of `DrupalExtended`. If this list matches yours, you can simple remove `Drupal` rulesets includes.

[unreleased]: https://github.com/olivierlacan/keep-a-changelog/compare/2.0.0-alpha2...HEAD
[2.0.0-alpha2]: https://github.com/Chi-teck/drupal-coder-extension/compare/2.0.0-alpha1...2.0.0-alpha2
[2.0.0-alpha1]: https://github.com/Chi-teck/drupal-coder-extension/releases/tag/2.0.0-alpha1