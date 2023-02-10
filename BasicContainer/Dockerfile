FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build-env
WORKDIR /BasicContainer

# Step 1 : Copy everything to container
COPY . ./
# Step 2 : Run dotnet restore to ensure all dependencies are in place
RUN dotnet restore
# Step 3 : Build the code and publish release
RUN dotnet publish -c Release -o out

# Build runtime image
FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /BasicContainer
COPY --from=build-env /BasicContainer/out .
ENTRYPOINT ["dotnet", "BasicContainer.dll"]
