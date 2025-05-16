# Etapa de build usando imagem .NET do Docker Hub
FROM amd64/dotnet:8.0-sdk AS build
WORKDIR /src
COPY . .
RUN dotnet publish AppLivrariaBlazor/AppLivrariaBlazor.csproj -c Release -o /app/publish

# Etapa de produção usando nginx
FROM nginx:stable-alpine AS final
WORKDIR /usr/share/nginx/html
# Copie os arquivos publicados do Blazor WebAssembly 
COPY --from=build /app/publish/wwwroot .
# Adicione configuração nginx para SPA
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80