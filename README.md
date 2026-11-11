# pizza-app-cs

REST API for a pizza shop, written in C# with ASP.NET Core controllers, Dapper and SQLite. Built as a school project to practise layered backend design without an ORM.

## What it does

- Customers, doughs, sizes and toppings (CRUD)
- Pizzas built from a dough, a size and any number of toppings: `POST/DELETE /pizzas/{pizzaId}/toppings/{toppingId}`
- Orders with one or more pizzas, with the total calculated from the parts

Each resource has a controller, a repository with hand-written SQL through Dapper, and request DTOs separate from the entities. `DbInit.cs` creates the schema on startup, and `pizza-api/db/app.db` ships with sample data.

## Run

Requires the .NET 10 SDK.

```sh
cd pizza-api
dotnet run    # http://localhost:5145
```

```sh
curl http://localhost:5145/pizzas
curl http://localhost:5145/orders/1
```

## Layout

- `pizza-api/Controllers/`: one controller per resource
- `pizza-api/Repositories/`: SQL queries, with loaders that assemble pizzas and orders from joined rows
- `pizza-api/Models/`: entities and DTOs
- `pizza-tui/`: start of a terminal client (Spectre.Console) for the API, not finished
