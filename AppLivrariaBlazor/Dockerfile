# Etapa de build
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

# Copia o arquivo .csproj primeiro e restaura as dependências
COPY AppLivrariaBlazor/AppLivrariaBlazor.csproj ./AppLivrariaBlazor/
RUN dotnet restore ./AppLivrariaBlazor/AppLivrariaBlazor.csproj

# Copia todos os arquivos
COPY . .

# Publica o projeto
WORKDIR /src/AppLivrariaBlazor
RUN dotnet publish -c Release -o /app/publish

# Etapa final
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS final
WORKDIR /app
COPY --from=build /app/publish .

# Executa a aplicação
ENTRYPOINT ["dotnet", "AppLivrariaBlazor.dll"]
