FROM mcr.microsoft.com/dotnet/sdk:6.0 as build-env
WORKDIR /src
COPY example.api.csproj .
RUN dotnet restore
COPY . .
RUN dotnet publish -c Release -o /publish

FROM mcr.microsoft.com/dotnet/aspnet:6.0 as runtime
WORKDIR /publish
COPY --from=build-env /publish .
EXPOSE 80

ENV ASPNETCORE_ENVIRONMENT=Production
ENTRYPOINT ["dotnet", "example.api.dll"]