# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Changed

- Require `drupal/coder ^9.0` and PHP `>=8.5`. Coder 8 / PHP CodeSniffer 3 is no
  longer supported.
- Stop excluding `SlevomatCodingStandard.Classes.BackedEnumTypeSpacing`,
  `SlevomatCodingStandard.Commenting.ForbiddenComments` and
  `SlevomatCodingStandard.ControlStructures.NewWithParentheses`, which Coder 9
  now enables in the `Drupal` standard itself.

## [2.0.0-rc2] - 2025-03-10

- Increase minimum version requirement for `slevomat/coding-standard` to
  `^8.16`.

## [2.0.0-rc1] - 2025-02-28

- The rule `SlevomatCodingStandard.TypeHints.UnionTypeHintFormat` has been
  replaced by `SlevomatCodingStandard.TypeHints.DNFTypeHintFormat`. Since the
  former is deprecated, it is explicitly excluded to remove the deprecation
  warning.

## [2.0.0-beta3] - 2024-04-03

### Changed

- Change ruleset name from “Drupal Extended” to “DrupalExtended”.
- Relative paths to extended rulesets were replaced by their names.
- Change package type from “library” to “phpcodesniffer-standard”. This will
  allow `dealerdirect/phpcodesniffer-composer-installer` to detect it and
  install the standard automatically.
- Update README.md on how use “DrupalExtended”.

## [2.0.0-beta2] - 2024-02-21

### Changed

- Updated configuration for rule `SlevomatCodingStandard.TypeHints.DeclareStrictTypes`
  to be compatible with [Drupal Coding Standards][drupal-cs-declare-strict-type].
  The rule from `drupal/coder` is overridden because it is disabling
  `SlevomatCodingStandard.TypeHints.DeclareStrictTypes.DeclareStrictTypesMissing`.

## [2.0.0-beta1] - 2023-08-11

Tagging alpha4 as beta1. No other changes.

## [2.0.0-alpha4] - 2023-04-25

### Added

- Added configuration for `SlevomatCodingStandard.Commenting.AnnotationName` to match Drupal Coding Standards.

## [2.0.0-alpha3] - 2023-04-03

### Added

- Added `CHANGELOG.md` file.

### Changed

- Update Composer dependencies.
- Excluded `SlevomatCodingStandard.Arrays.AlphabeticallySortedByKeys`.
- Excluded `SlevomatCodingStandard.Exceptions.ReferenceThrowableOnly`.

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
    <rule ref="DrupalExtended"/>
    ```
3. If you have `<rule ref="vendor/drupal/coder/coder_sniffer/Drupal"/>` and/or `<rule ref="vendor/drupal/coder/coder_sniffer/DrupalPractice"/>`  without rules overrides — you can remove them, they're now included by default in `DrupalExtended`.
4. If you have rules overrides for `Drupal` sniffers, take a look at [current overrides](https://github.com/Chi-teck/drupal-coder-extension/blob/2.x/DrupalExtended/ruleset.xml#L5-L16) of `DrupalExtended`. If this list matches yours, you can simple remove `Drupal` rulesets includes.

[unreleased]: https://github.com/olivierlacan/keep-a-changelog/compare/2.0.0-rc2...HEAD
[2.0.0-rc2]: https://github.com/Chi-teck/drupal-coder-extension/compare/2.0.0-rc1...2.0.0-rc2
[2.0.0-rc1]: https://github.com/Chi-teck/drupal-coder-extension/compare/2.0.0-beta3...2.0.0-rc1
[2.0.0-beta3]: https://github.com/Chi-teck/drupal-coder-extension/compare/2.0.0-beta2...2.0.0-beta3
[2.0.0-beta2]: https://github.com/Chi-teck/drupal-coder-extension/compare/2.0.0-beta1...2.0.0-beta2
[2.0.0-beta1]: https://github.com/Chi-teck/drupal-coder-extension/compare/2.0.0-alpha4...2.0.0-beta1
[2.0.0-alpha4]: https://github.com/Chi-teck/drupal-coder-extension/compare/2.0.0-alpha3...2.0.0-alpha4
[2.0.0-alpha3]: https://github.com/Chi-teck/drupal-coder-extension/compare/2.0.0-alpha2...2.0.0-alpha3
[2.0.0-alpha2]: https://github.com/Chi-teck/drupal-coder-extension/compare/2.0.0-alpha1...2.0.0-alpha2
[2.0.0-alpha1]: https://github.com/Chi-teck/drupal-coder-extension/releases/tag/2.0.0-alpha1

[drupal-cs-declare-strict-type]: https://www.drupal.org/node/3402544
