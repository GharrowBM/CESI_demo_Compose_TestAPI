FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build

WORKDIR /source

COPY TestAPI.WebAPI.csproj .

RUN dotnet restore

COPY . .

RUN dotnet publish -o build -c Release 

FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS base

WORKDIR /app

COPY --from=build /source/build .

EXPOSE 80

CMD [ "dotnet", "TestAPI.WebAPI.dll"]