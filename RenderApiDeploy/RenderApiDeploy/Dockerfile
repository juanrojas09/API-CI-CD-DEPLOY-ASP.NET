#See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.
#
#FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
#USER app
#WORKDIR /app
#EXPOSE 8080
#
#FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
#ARG BUILD_CONFIGURATION=Release
#WORKDIR /src
#COPY ["RenderApiDeploy/RenderApiDeploy.csproj", "RenderApiDeploy/"]
#RUN dotnet restore "./RenderApiDeploy/./RenderApiDeploy.csproj"
#COPY . .
#WORKDIR "/src/RenderApiDeploy"
#RUN dotnet build "./RenderApiDeploy.csproj" -c $BUILD_CONFIGURATION -o /app/build
#
#FROM build AS publish
#ARG BUILD_CONFIGURATION=Release
#RUN dotnet publish "./RenderApiDeploy.csproj" -c $BUILD_CONFIGURATION -o /app/publish /p:UseAppHost=false
#
#FROM base AS final
#WORKDIR /app
#COPY --from=publish /app/publish .
#ENTRYPOINT ["dotnet", "RenderApiDeploy.dll"]


FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
WORKDIR /app
EXPOSE 8080

FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
ARG BUILD_CONFIGURATION=Release
WORKDIR /src

# Copia el archivo .csproj y restaura las dependencias
COPY ["RenderApiDeploy/RenderApiDeploy/RenderApiDeploy.csproj", "RenderApiDeploy/RenderApiDeploy/"]
RUN dotnet restore "RenderApiDeploy/RenderApiDeploy/RenderApiDeploy.csproj"

# Copia todos los archivos restantes
COPY RenderApiDeploy/RenderApiDeploy/. ./RenderApiDeploy/

# Compila el proyecto
WORKDIR "/src/RenderApiDeploy/RenderApiDeploy"
RUN dotnet build "RenderApiDeploy.csproj" -c $BUILD_CONFIGURATION -o /app/build

FROM build AS publish
ARG BUILD_CONFIGURATION=Release
RUN dotnet publish "RenderApiDeploy.csproj" -c $BUILD_CONFIGURATION -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "RenderApiDeploy.dll"]
