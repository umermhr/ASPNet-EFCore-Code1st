# ASP.NET Core Web API with Entity Framework Core (Code First Approach)

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
  - [Clone the Repository](#clone-the-repository)
  - [Set Up the Database](#set-up-the-database)
  - [Run the Application](#run-the-application)
- [API Endpoints](#api-endpoints)
- [Entity Framework Core Code First Approach](#entity-framework-core-code-first-approach)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

This is a sample **ASP.NET Core Web API** project that demonstrates how to build RESTful APIs using **Entity Framework Core** with the **Code First Approach**. The project includes database migrations, models, controllers, and services to help you quickly get started with building scalable APIs.

The application uses **SQL Server** as the database provider, but you can easily switch to another provider like SQLite or PostgreSQL if needed.

---

## Features

- **RESTful API Design**: Follows best practices for building APIs.
- **Entity Framework Core**: Uses the Code First approach to define models and generate database schemas.
- **Database Migrations**: Easily manage schema changes using EF Core migrations.
- **Dependency Injection**: Built-in support for dependency injection.
- **Swagger Integration**: API documentation with Swagger UI.
- **Validation**: Data validation using Data Annotations and Fluent Validation.

---

## Prerequisites

Before running this project, ensure you have the following installed:

- [.NET SDK 6.0 or later](https://dotnet.microsoft.com/download)
- [SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads) (or any other supported database provider)
- [Visual Studio Code](https://code.visualstudio.com/) or [Visual Studio](https://visualstudio.microsoft.com/) (optional)
- [Postman](https://www.postman.com/) or any API testing tool (optional)

---

## Getting Started

### Clone the Repository

```bash
git clone https://github.com/yourusername/aspnetcore-webapi-efcore.git
cd aspnetcore-webapi-efcore
```

### Set Up the Database

1. **Update the Connection String**:
   Open the `appsettings.json` file and update the `DefaultConnection` string with your SQL Server credentials.

   ```json
   "ConnectionStrings": {
       "DefaultConnection": "Server=your_server_name;Database=YourDatabaseName;Trusted_Connection=True;"
   }
   ```

2. **Apply Migrations**:
   Run the following commands to apply the initial database migrations:

   ```bash
   dotnet ef database update
   ```

   This will create the database and tables based on your models.

### Run the Application

Start the application using the following command:

```bash
dotnet run
```

By default, the API will be available at: `https://localhost:5001`.

You can also use Swagger UI to test the API by navigating to: `https://localhost:5001/swagger`.

---

## API Endpoints

| HTTP Method | Endpoint              | Description                     |
|-------------|-----------------------|---------------------------------|
| GET         | `/api/products`       | Get all products                |
| GET         | `/api/products/{id}`  | Get a product by ID             |
| POST        | `/api/products`       | Create a new product            |
| PUT         | `/api/products/{id}`  | Update an existing product      |
| DELETE      | `/api/products/{id}`  | Delete a product                |

*(Replace `/api/products` with your actual endpoints)*

---

## Entity Framework Core Code First Approach

The project follows the **Code First** approach, where the database schema is generated from the C# classes (models). Here's a brief overview of how it works:

1. **Define Models**: Create C# classes that represent your database tables.
   
   ```csharp
   public class Product
   {
       public int Id { get; set; }
       public string Name { get; set; }
       public decimal Price { get; set; }
   }
   ```

2. **Create DbContext**: Define a `DbContext` class that manages the entity objects during runtime.

   ```csharp
   public class ApplicationDbContext : DbContext
   {
       public ApplicationDbContext(DbContextOptions<ApplicationDbContext> options) : base(options) { }

       public DbSet<Product> Products { get; set; }
   }
   ```

3. **Add Migrations**: Use EF Core CLI tools to create and apply migrations.

   ```bash
   dotnet ef migrations add InitialCreate
   dotnet ef database update
   ```

4. **Update Models**: Whenever you make changes to your models, create new migrations and update the database.

---

## Contributing

We welcome contributions! If you'd like to contribute to this project, please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/YourFeatureName`).
3. Commit your changes (`git commit -m 'Add some feature'`).
4. Push to the branch (`git push origin feature/YourFeatureName`).
5. Open a pull request.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---
