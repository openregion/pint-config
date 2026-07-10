# OpenRegion Pint Config

Reusable [Laravel Pint](https://laravel.com/docs/pint) configuration for Open Region PHP projects.

The configuration starts with Pint's `laravel` preset and applies Open Region's shared PHP style. Laravel rules with different Open Region behavior are overridden, and additional Open Region rules are included as well.

## Installation

Install the package as a development dependency:

```shell
composer require --dev openregion/pint-config
```

The package installs a compatible Laravel Pint version automatically.

## Usage

Create `pint.json` in the root of your project and extend the shared configuration:

```json
{
    "extend": "vendor/openregion/pint-config/pint.json"
}
```

Run Pint normally:

```shell
vendor/bin/pint
```

Use test mode in CI or pre-commit checks:

```shell
vendor/bin/pint --test
```

### Project-specific rules

Add project-specific rules and finder options to the local `pint.json`:

```json
{
    "extend": "vendor/openregion/pint-config/pint.json",
    "rules": {
        "single_quote": false
    },
    "exclude": [
        "generated"
    ]
}
```

### Direct usage

The shared configuration can also be selected without a local `pint.json`:

```shell
vendor/bin/pint --config=vendor/openregion/pint-config/pint.json
```

## Rule baseline

The current rule comparison uses:

- Laravel Pint 1.29.3 and its `laravel` preset;
- PHP CS Fixer 3.95.8, bundled with that Pint release.

Semantically equivalent configurations are left to the Laravel preset. The published `pint.json` contains explicit rule overrides and additions instead of another preset, keeping the inheritance order predictable.

## License

This package is open-sourced software licensed under the [MIT license](LICENSE).
