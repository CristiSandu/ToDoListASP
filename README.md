# ToDoListAPI

## Steps to set Database with code first:

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

## Homework

A ASP .NET API with a SQL Server database that contains next tables:

- Users Model
- Team ex: Team1, Team2
- Position ex: Dev, HR, Manager, etc..

GET, POST, PUT, DELETE for every table  
Possibility to get Users grouped by: team, position.

## Links

- Workshop 18.08.2023 https://youtu.be/Th0Hznj2hTA?wt.mc_id=studentamb_61984 https://youtu.be/Th0Hznj2hTA?wt.mc_id=studentamb_61984
- DB installation on docker https://ocw.cs.pub.ro/courses/bd2/resurse/docker
- SSMS https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16?wt.mc_id=studentamb_61984
- Virtual in C# https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/virtual?wt.mc_id=studentamb_61984
