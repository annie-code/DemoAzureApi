##See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.
#
##Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
##For more information, please see https://aka.ms/containercompat
#
#FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
#WORKDIR /app
#EXPOSE 80
#EXPOSE 443
#
#FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
#WORKDIR /src
#COPY ["DemoAzureApi/DemoAzureApi.csproj", "DemoAzureApi/"]
#RUN dotnet restore "DemoAzureApi/DemoAzureApi.csproj"
#COPY . .
#WORKDIR "/src/DemoAzureApi"
#RUN dotnet build "DemoAzureApi.csproj" -c Release -o /app/build
#
#FROM build AS publish
#RUN dotnet publish "DemoAzureApi.csproj" -c Release -o /app/publish
#
#FROM base AS final
#WORKDIR /app
#COPY --from=publish /app/publish .
#ENTRYPOINT ["dotnet", "DemoAzureApi.dll"]



#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

#Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
#For more information, please see https://aka.ms/containercompat

FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
#
#FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
#WORKDIR /src
#COPY ["DemoDocker/DemoDocker.csproj", "DemoDocker/"]
#RUN dotnet restore "DemoDocker/DemoDocker.csproj"
#COPY . .
#WORKDIR "/src/DemoDocker"
#RUN dotnet build "DemoDocker.csproj" -c Release -o /app/build
#
#FROM build AS publish
#RUN dotnet publish "DemoDocker.csproj" -c Release -o /app/publish
#
#FROM base AS final
#WORKDIR /app
#COPY --from=publish /app/publish .
#ENTRYPOINT ["dotnet", "DemoDocker.dll"]

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
#COPY ["DemoAzureApi/DemoAzureApi.csproj", "DemoAzureApi/"]
#COPY /DemoAzureApi/DemoAzureApi.csproj .
COPY DemoAzureApi.csproj .
RUN dotnet restore
COPY . .
RUN dotnet publish -c release -o /app

FROM mcr.microsoft.com/dotnet/aspnet:5.0
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet", "DemoAzureApi.dll"]
