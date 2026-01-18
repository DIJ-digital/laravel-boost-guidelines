## Integration Conventions

### Guidelines
- Place integrations in `app/Integrations/{ServiceName}/`.
- Structure: `Client/` (Factory, PendingRequest), `Resources/` (Clients, DTOs), `Facade/`.
- Use the Facade for all API calls within Resource Clients.
- Resource Clients should inject `Illuminate\Http\Request` to handle filters and pagination parameters.
- Return `Illuminate\Pagination\LengthAwarePaginator` for index methods.
- Use DTOs for all data returned from the API.
- Always include a `transformArray` helper for mapping collections to DTOs.
- Use constructor property promotion with `readonly` for DTOs.
- Always include a static `fromArray()` method in DTOs.

### Example implementation
```php
class UserClient
{
    public function __construct(
        private readonly Request $request
    ) {}

    public function index(): LengthAwarePaginator
    {
        $response = ExampleApi::get('users', $this->request->all());

        return new LengthAwarePaginator(
            items: $this->transformArray($response['data']),
            total: $response['meta']['total'] ?? 0,
            perPage: $response['meta']['per_page'] ?? 15,
            currentPage: $response['meta']['current_page'] ?? 1,
            options: [
                'path' => $this->request->url(),
                'query' => $this->request->query(),
            ]
        );
    }

    public function show(int $id): UserDTO
    {
        $response = ExampleApi::get("users/{$id}");

        return UserDTO::fromArray($response['data']);
    }

    private function transformArray(array $data): array
    {
        return array_map(
            fn (array $item): UserDTO => UserDTO::fromArray($item),
            $data
        );
    }
}

readonly class UserDTO
{
    public function __construct(
        public int $id,
        public string $name,
    ) {}

    public static function fromArray(array $data): self
    {
        return new self(
            id: $data['id'],
            name: $data['name'],
        );
    }
}
```
