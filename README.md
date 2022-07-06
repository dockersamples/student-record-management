# Building a Student Database using .NET and Docker


This repository shows you how to containerize a .NET application using Docker Compose. The application used in this blog is a Webapp communicating with a Postgresql database. When the page is loaded, it will query the Student table for the record with ID and display the name of student on the page.





## Getting Started


### Clone the repository


```
git clone https://github.com/ajeetraina/students-database-dotnet-docker
cd students-database-dotnet-docker
```

```
docker build -t mywebapp .
[+] Building 5.0s (14/14) FINISHED                                                                                          
 => [internal] load build definition from Dockerfile                                                                   0.0s
 => => transferring dockerfile: 292B                                                                                   0.0s
 => [internal] load .dockerignore                                                                                      0.0s
 => => transferring context: 2B                                                                                        0.0s
 => [internal] load metadata for mcr.microsoft.com/dotnet/aspnet:latest                                                0.1s
 => [internal] load metadata for mcr.microsoft.com/dotnet/sdk:latest                                                   0.1s
 => [internal] load build context                                                                                      0.2s
 => => transferring context: 8.81MB                                                                                    0.2s
 => CACHED [base 1/3] FROM mcr.microsoft.com/dotnet/aspnet@sha256:38a3a3f5a8bf00e79bff52754b5eb29522a998cbd9734ef8b87  0.0s
 => CACHED [build 1/5] FROM mcr.microsoft.com/dotnet/sdk@sha256:6d035a4d0893c8d9e38b03e811b87e7689dd9b2763a4fb3585d7e  0.0s
 => [build 2/5] COPY . ./src                                                                                           0.0s
 => [build 3/5] WORKDIR /src                                                                                           0.0s
 => [build 4/5] RUN dotnet build -o /app                                                                               3.0s
 => [build 5/5] RUN dotnet publish -o /publish                                                                         1.2s 
 => [base 2/3] COPY --from=build  /publish /app                                                                        0.0s 
 => [base 3/3] WORKDIR /app                                                                                            0.0s 
 => exporting to image                                                                                                 0.0s 
 => => exporting layers                                                                                                0.0s 
 => => writing image sha256:0b2f381d01c49f3a85bf5cd00bd5914207dbf62f2464737ef015157af9e6175e                           0.0s 
 => => naming to docker.io/library/mywebapp
 ```


```
docker images
REPOSITORY                                  TAG              IMAGE ID       CREATED          SIZE
mywebapp                                    latest           0b2f381d01c4   6 seconds ago    224MB
```

### Running the app

```
docker run -d -p 5000:80 mywebapp
```

```
0d5cf0d60ef5d05a9fba0e2985b1b7e76ef7b44e4318065957548a984ecf2b0c
ajeetraina@Docker-Ajeet-Singh-Rainas-MacBook-Pro myWebApp % docker ps
CONTAINER ID   IMAGE                                      COMMAND                  CREATED         STATUS         PORTS                                                                                                 NAMES
0d5cf0d60ef5   mywebapp                                   "./myWebApp"             3 seconds ago   Up 2 seconds   0.0.0.0:5000->80/tcp                                                                                  goofy_pare
```


## Reference:

- [Blog Post](https://www.docker.com/blog/building-multi-container-net-app-using-docker-desktop/)
