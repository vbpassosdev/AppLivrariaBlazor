# Use a imagem oficial do .NET SDK para build
FROM mcr.microsoft.com/dotnet/sdk:.0 AS build
WORKDIR /src
COPY . .
RUN dotnet publish -c Release -o /app

# Use uma imagem runtime para execução
FROM mcr.microsoft.com/dotnet/aspnet:7.0
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet", "AppLivrariaBlazor.dll"]
