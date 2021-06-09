goto this folder
dotnet new sln
dotnet new webapi -o API
dotnet sln add API

--> open this folder in vscode



Create a folder Entities
Create an entity
ctrl+shift+p => open nuget gallery
Microsoft.EntityFrameworkCore.Sqlite ==> install it

create folder Data
Create class DataContext

goto startup.cs
public void ConfigureServices(IServiceCollection services)
        {

            services.AddControllers();
            services.AddDbContext<DataContext>(options =>
            {
                options.UseSqlite(_config.GetConnectionString("DefaultConnection"));
            });


in the appsettings,
"ConnectionStrings": {
    "DefaultConnection":"Data source=datingApp.db"
  },



install Microsoft.EntityFrameworkCore.Design
goto nuget.org
search dotnet-ef
copy the global install tool command (dotnet tool install --global dotnet-ef --version 5.0.7)
run it in the terminal
inside the api app, run dotnet ef migrations add InitialCreate -o Data/Migrations in the terminal

dotnet ef database update
