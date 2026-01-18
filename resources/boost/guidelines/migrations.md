## Migration Conventions

### Guidelines
- Always use specific timestamp definitions instead of the default `$table->timestamps()`.
- Ensure `created_at` uses the current timestamp.
- Ensure `updated_at` uses the current timestamp and updates on every modification.

### Example implementation
```php
public function up(): void
{
    Schema::create('users', function (Blueprint $table) {
        $table->id();
        $table->string('name');
        
        $table->timestamp(column: 'created_at')->useCurrent();
        $table->timestamp(column: 'updated_at')->useCurrent()->useCurrentOnUpdate();
    });
}
```
