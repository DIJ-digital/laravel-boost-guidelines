## Form Request Conventions

### Guidelines
- **Always** use Form Request classes for validation.
- Store in `app/Http/Requests/{Resource}/{Action}Request.php`.
- Use the same resource/action naming system as controllers.
- Use array-based validation rules (no pipe strings).
- Use `validated()` in controllers to retrieve data.

### Example implementation
```php
namespace App\Http\Requests\User;

class StoreRequest extends FormRequest
{
    public function rules(): array
    {
        return [
            'email' => ['required', 'email', 'unique:users'],
        ];
    }
}
```
