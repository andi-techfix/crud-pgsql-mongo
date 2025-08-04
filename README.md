# СRUD MONGO+POSTGRES MONOREPO

# Local Setup
## Setup Environment 
1. 🔗[.NET 8 SDK](https://dotnet.microsoft.com/en-us/download) depending on your OS
2. 🔗[Docker Engine](https://docs.docker.com/engine/install/) depending on your OS
3. 🔗[Postman](https://www.postman.com/downloads/) *optionally        
----
## Runing project
```sh
git clone https://github.com/andi-techfix/crud-pgsql-mongo.git
cd crud-pgsql-mongo

git submodule sync
git submodule update --init --recursive

docker-compose up --build
```

## Run project
```sh
dotnet run
```
## Run test
In project root just run command
```sh
dotnet test
```

1. How to add migrations?
 1.1 Add next environment variables to cmd(cmd open in db project root)
 Windows - 
 ```sh
./env_variables.ps1
 ```
 UNIX - 
 ```sh
source ./env_variables.sh
```

1.2 Go to db project and run command 
 ```sh
 cd Infrastructure
 dotnet ef migrations add *MIGRATION_NAME* --startup-project ../UserService  
 ```
1.3 To Manually update database after a successful migration
```sh
dotnet ef database update --startup-project ../UserService
```
1.4 Migration can be run automatically when application starts, 
if you want to disable this feature, you can do it in ServiceInjector.cs file and comment RunDbMigrations method
```
