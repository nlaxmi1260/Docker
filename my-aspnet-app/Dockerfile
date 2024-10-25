# Use the official .NET SDK image to build the application
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build

# Set the working directory inside the container
WORKDIR /src

# Copy the .csproj file and restore the dependencies
COPY *.csproj ./
RUN dotnet restore

# Copy the rest of the application source code
COPY . .

# Build the application and publish the output to the /app directory
RUN dotnet publish -c Release -o /app

# Use the official ASP.NET Core runtime image for the final stage
FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS runtime

# Set the working directory in the runtime container
WORKDIR /app

# Copy the build output from the previous stage to the runtime container
COPY --from=build /app .

# Expose port 80 for the application
EXPOSE 80

# Set the entry point for the application
ENTRYPOINT ["dotnet", "my-aspnet-app.dll"]