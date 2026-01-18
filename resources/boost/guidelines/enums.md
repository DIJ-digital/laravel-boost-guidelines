## Enum Conventions

### Guidelines
- Store in `app/Enums/`.
- Case names must always be UPPERCASE.
- Use `Rule::enum()` for validation.

### Example implementation
```php
enum Status: string
{
    case PENDING = 'pending';
    case ACTIVE = 'active';
}
```
