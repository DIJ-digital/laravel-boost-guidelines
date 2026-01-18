## Action Conventions

### Guidelines
- Store in `app/Actions/`.
- Use a single `handle()` method.
- Inject actions into controllers via constructor injection.
- Naming: `{Verb}{Resource}Action` (e.g. `CreateUserAction`).

### Example implementation
```php
class CreateUserAction
{
    public function handle(array $data): User
    {
        return User::create($data);
    }
}
```
