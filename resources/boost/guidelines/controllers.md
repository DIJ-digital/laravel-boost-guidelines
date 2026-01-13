# Controller Conventions

## Invokable Controllers

Use **invokable controllers** with a single `__invoke()` method per controller.

## Structure

Place controllers in: `app/Http/Controllers/{Resource}/{Action}Controller.php`

Use **CRUD-style names** for controllers: `IndexController`, `ShowController`, `StoreController`, `UpdateController`, `DestroyController`.

```
app/Http/Controllers/
└── Resource/
    ├── IndexController.php
    ├── ShowController.php
    ├── StoreController.php
    ├── UpdateController.php
    └── DestroyController.php
```

## Creating Controllers

```bash
php artisan make:controller {Resource}/{Action}Controller --invokable
```

## Keep Controllers Thin

Controllers handle HTTP requests only. Delegate business logic to Services or Actions.
