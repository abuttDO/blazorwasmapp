# blazorwasmapp
Blazor WASM APP deploying using Dockerfile

Used below .Net doc to deploy:
```
https://learn.microsoft.com/en-us/aspnet/core/blazor/tutorials/build-a-blazor-app?view=aspnetcore-6.0&pivots=server
```

DOCkerfile is placed in Client folder from where I started the server using command

```
dotnet watch run
```

## Deploy using a Dockerfile

### Building Docker Image Locally

```
docker build -t <imagename> .
```

Failed with below error:

```
Step 1/16 : FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
 ---> 1cde569b1014
Step 2/16 : WORKDIR /app
 ---> Using cache
 ---> 8c5776c58761
Step 3/16 : EXPOSE 80
 ---> Using cache
 ---> 139a0ef84cb8
Step 4/16 : EXPOSE 443
 ---> Using cache
 ---> ef31a31fbd5a
Step 5/16 : FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
 ---> a193959b8fd7
Step 6/16 : WORKDIR /src
 ---> Using cache
 ---> 9946bdf2dd0f
Step 7/16 : COPY ["TodoList.Client.csproj", "."]
 ---> Using cache
 ---> 136b684d1e7c
Step 8/16 : RUN dotnet restore "TodoList.Client.csproj"
 ---> Using cache
 ---> c1f9ebbc6e4d
Step 9/16 : COPY . .
 ---> 8e2e93062b49
Step 10/16 : RUN dotnet build "TodoList.Client.csproj" -c Release -o /app/build
 ---> Running in f5b6ae149683
MSBuild version 17.3.2+561848881 for .NET
  Determining projects to restore...
  Skipping project "/Shared/TodoList.Shared.csproj" because it was not found.
  Skipping project "/Shared/TodoList.Shared.csproj" because it was not found.
  Restored /src/TodoList.Client.csproj (in 510 ms).
/usr/share/dotnet/sdk/6.0.403/Microsoft.Common.CurrentVersion.targets(2066,5): warning : The referenced project '../Shared/TodoList.Shared.csproj' does not exist. [/src/TodoList.Client.csproj]
/src/Pages/FetchData.razor(2,16): error CS0234: The type or namespace name 'Shared' does not exist in the namespace 'TodoList' (are you missing an assembly reference?) [/src/TodoList.Client.csproj]
/src/Pages/FetchData.razor(41,13): error CS0246: The type or namespace name 'WeatherForecast' could not be found (are you missing a using directive or an assembly reference?) [/src/TodoList.Client.csproj]

Build FAILED.

/usr/share/dotnet/sdk/6.0.403/Microsoft.Common.CurrentVersion.targets(2066,5): warning : The referenced project '../Shared/TodoList.Shared.csproj' does not exist. [/src/TodoList.Client.csproj]
/src/Pages/FetchData.razor(2,16): error CS0234: The type or namespace name 'Shared' does not exist in the namespace 'TodoList' (are you missing an assembly reference?) [/src/TodoList.Client.csproj]
/src/Pages/FetchData.razor(41,13): error CS0246: The type or namespace name 'WeatherForecast' could not be found (are you missing a using directive or an assembly reference?) [/src/TodoList.Client.csproj]
    1 Warning(s)
    2 Error(s)

Time Elapsed 00:00:05.60
The command '/bin/sh -c dotnet build "TodoList.Client.csproj" -c Release -o /app/build' returned a non-zero code: 1
```