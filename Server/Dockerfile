FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /app
COPY ["Server/TodoList.Server.csproj", "Server/"]
COPY ["Client/TodoList.Client.csproj", "Client/"]
COPY ["Shared/TodoList.Shared.csproj", "Shared/"]
RUN dotnet restore "Server/TodoList.Server.csproj"
COPY . .
WORKDIR "/app/Server"
RUN dotnet build "TodoList.Server.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "TodoList.Server.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "TodoList.Server.dll"]
