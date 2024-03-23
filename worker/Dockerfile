# Use a specific version of the .NET SDK that supports .NET 7.0
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build

# Set the working directory in the container
WORKDIR /app

# Copy the project files to the container
COPY . .

# Build the project
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS runtime
WORKDIR /app
COPY --from=build /app/out ./

EXPOSE 80

ENTRYPOINT ["dotnet", "Worker.dll"]
