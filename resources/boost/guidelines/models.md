## Model Conventions

### Guidelines
- Use `protected $guarded = [];` instead of `$fillable`.
- Use the `#[UseEloquentBuilder(class)]` attribute when using a custom builder.

### Example implementation
```php
#[UseEloquentBuilder(UserBuilder::class)]
class User extends Model
{
    protected $guarded = [];

    public function posts(): HasMany
    {
        return $this->hasMany(Post::class);
    }
}
```
