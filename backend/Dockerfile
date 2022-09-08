FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY backend.csproj .
RUN dotnet restore
COPY . .
RUN dotnet publish -c release -o /app

# reducing files by publishing only needed artifacts & dlls instead of source code
FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
EXPOSE 80
EXPOSE 443 
COPY --from=build /app .
ENTRYPOINT [ "dotnet","backend.dll" ]