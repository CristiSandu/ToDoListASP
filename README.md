# ToDoListAPI

Steps to set Database with code first:

- Install this NuGets:
  - Microsoft.EntityFrameworkCore
  - Microsoft.EntityFrameworkCore.SqlServer
  - Microsoft.EntityFrameworkCore.Tools
- In Program.cs add this :

```csharp
builder.Services.AddDbContext<TodoContext>(opt => opt.UseSqlServer(builder.Configuration.GetSection("ConnectionString").Value));
```

where ConnectionString is in appsettings.json

- Define the Context -> ex: TodoContext.cs
- Add MigrationsDbContextFactory.cs
- Add Models for database

```csharp
public class TodoItem
{
    public long Id { get; set; }
    public string? Name { get; set; }
    public bool IsComplete { get; set; }
    public string? Secret { get; set; }
}
```

- Add Models as sets in Context

```csharp
    public DbSet<TodoItem> TodoItems { get; set; } = null!;
    public DbSet<User> Users { get; set; } = null!;
```

- Run initial migration command

```
 Add-Migration InitialMigration
```

- Run update command to database

```
dotnet ef database update --connection "connectionString"
```

- Run migration and update after any change on the Models

```
Add-Migration "MigrationName"
dotnet ef database update --connection "connectionString"
```
