# Use official .NET SDK image for building
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app

# Copy the project files
COPY ["YourProject.API.csproj", "./"]
RUN dotnet restore

# Copy everything else and build the application
COPY . .
RUN dotnet publish -c Release -o /out

# Use runtime image
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
WORKDIR /app
COPY --from=build /out .

# Expose port and set entry point
EXPOSE 8080
ENTRYPOINT ["dotnet", "YourProject.API.dll"]