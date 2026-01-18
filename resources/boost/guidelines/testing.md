## Testing Conventions

### Guidelines
- Always structure tests using `// Arrange`, `// Act`, and `// Assert` comments.

### Example implementation
```php
public function testStatusCanBeUpdated(): void
{
    // Arrange
    $post = Post::factory()->create();

    // Act
    $post->update(['status' => 'published']);

    // Assert
    $this->assertEquals('published', $post->status);
}
```
