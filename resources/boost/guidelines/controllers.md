## Controller Conventions

### Guidelines
- **Always** use invokable controllers (`__invoke`).
- Store in `app/Http/Controllers/{Resource}/{Action}Controller.php`.
- Keep controllers thin; delegate logic to Actions or Services.
- Use Form Requests for all validation.

### Example implementation
```php
class StoreController extends Controller
{
    public function __invoke(StoreRequest $request, CreateUserAction $action): RedirectResponse
    {
        $action->handle($request->validated());

        return redirect()->route('users.index');
    }
}
```
