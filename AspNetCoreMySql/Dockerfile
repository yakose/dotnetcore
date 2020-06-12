FROM mcr.microsoft.com/dotnet/core/sdk:2.1 AS build-env
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out

# Build runtime image
FROM mcr.microsoft.com/dotnet/core/aspnet:2.1
WORKDIR /app
COPY --from=build-env /app/out .

EXPOSE 80/tcp
ENV ASPNETCORE_URLS http://*:80
HEALTHCHECK --interval=30s --timeout=3s  --retries=1 CMD curl --silent --fail http://localhost:80/hc || exit 1

ENTRYPOINT ["dotnet", "AspNetCoreMySql.dll"]
