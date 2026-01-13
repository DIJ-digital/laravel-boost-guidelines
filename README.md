# Laravel Boost Guidelines

Shared AI guidelines for Laravel Boost in DIJ Digital projects.

## Installation

```bash
composer require dij-digital/laravel-boost-guidelines --dev
```

Then enable the guidelines by adding them to your `boost.json`:

```json
{
    "guidelines": [
        "dij-digital/laravel-boost-guidelines"
    ]
}
```

Or run `php artisan boost:install` and select the package when prompted for third-party guidelines.

Finally, update your AI guidelines:

```bash
php artisan boost:update
```

The guidelines will now be included in your AI context.

## Adding Guidelines

Add `.md` files to `resources/boost/guidelines/`:

```
resources/
└── boost/
    └── guidelines/
        └── controllers.md
        └── testing.md
        └── services.blade.php
```
