# blazorwasmapp
Blazor WASM APP deploying using Dockerfile

Used below .Net doc to deploy:
```
https://learn.microsoft.com/en-us/aspnet/core/blazor/tutorials/build-a-blazor-app?view=aspnetcore-6.0&pivots=server
```

Docker file is placed in the Server project since the asp core server will be serving the wasm client project

To run the project you should be in the Server directory
```
dotnet watch run
```

## Deploy using a Dockerfile

### Building Docker Image Locally

Run from main solution folder
```
docker build -t <imagename> -f ./Server/Dockerfile .
```