FROM mcr.microsoft.com/dotnet/sdk:5.0 AS dotnetsdk
WORKDIR /source
COPY *.csproj ./
RUN dotnet restore
COPY . ./
RUN dotnet publish -c Release -o out
FROM mcr.microsoft.com/dotnet/aspnet:5.0
WORKDIR /build
EXPOSE 80
COPY --from=dotnetsdk /source/out ./
ENTRYPOINT ["dotnet", "8488_cw1_api.dll"]