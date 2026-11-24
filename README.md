# OpenRegion Pint Config

Reusable [Laravel Pint](https://laravel.com/docs/pint) configuration for Open Region PHP projects.

The configuration starts with Pint's `laravel` preset, applies PER Coding Style 3.0, and gives Open Region's explicit PHP CS Fixer rules the highest priority.

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

The first group in `pint.json` contains the rules from `@PER-CS3x0` in PHP CS Fixer 3.95.8, bundled with Pint 1.29.3. The second group contains the explicit rules from Open Region's [PHP CS Fixer config 1.2.0](https://github.com/openregion/php-cs-fixer-config/blob/1.2.0/src/Config.php). Rules shared by both groups appear once with their Open Region settings.

The final two entries disable Laravel preset rules to match that release. Pint keeps PHPDoc types that repeat a signature and formats logical negation as `!$ready`.

Pint merges the Laravel preset with the JSON rules before PHP CS Fixer expands named sets. A literal `@PER-CS3x0` entry would overwrite some explicit settings, including alphabetical import sorting. Listing the individual rules preserves the intended precedence and allows projects to override them via `extend`.

## License

This package is open-sourced software licensed under the [MIT license](LICENSE).
