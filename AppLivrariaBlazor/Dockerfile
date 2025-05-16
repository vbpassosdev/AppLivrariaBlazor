FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src
COPY AppLivrariaBlazor/AppLivrariaBlazor.csproj ./AppLivrariaBlazor/
RUN dotnet restore ./AppLivrariaBlazor/AppLivrariaBlazor.csproj
COPY . .
WORKDIR /src/AppLivrariaBlazor
RUN dotnet publish -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS final
WORKDIR /app
COPY --from=build /app/publish .

# Configurações específicas para o Render
ENV ASPNETCORE_URLS=http://+:80
ENV PORT=80
EXPOSE 80

ENTRYPOINT ["dotnet", "AppLivrariaBlazor.dll"]