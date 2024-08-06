# Ouput
@Sofiaaa20 ➜ /workspaces/labs-docker-dev (main) $ docker pull nginx
Using default tag: latest
latest: Pulling from library/nginx
efc2b5ad9eec: Pull complete 
8fe9a55eb80f: Pull complete 
045037a63be8: Pull complete 
7111b42b4bfa: Pull complete 
3dfc528a4df9: Pull complete 
9e891cdb453b: Pull complete 
0f11e17345c5: Pull complete 
Digest: sha256:6af79ae5de407283dcea8b00d5c37ace95441fd58a8b1d2aa1ed93f5511bb18c
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest

# Running our container

77ddf35d886188bdd1d93a57d526353f9d7878beab71d826b514127211c937c7

#  Ejecuta un contenedor de Ubuntu en modo interactivo:

@Sofiaaa20 ➜ /workspaces/labs-docker-dev (main) $ docker run -it ubuntu bashUnable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
9c704ecd0c69: Pull complete 
Digest: sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Status: Downloaded newer image for ubuntu:latest
root@4c04d3eb60b5:/# 


# Eliminar 

@Sofiaaa20 ➜ /workspaces/labs-docker-dev (main) $ docker ps -a
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS                       PORTS                                   NAMES
4c04d3eb60b5   ubuntu    "bash"                   4 minutes ago   Exited (130) 4 seconds ago   

# ---------------------------------------------------------------------------------------------

# Docker Build

@Sofiaaa20 ➜ /workspaces/labs-docker-dev (main) $ docker build -t ubuntu-updated:latest .
[+] Building 33.5s (9/9) FINISHED                                                                            docker:default
 => [internal] load build definition from Dockerfile                                                                   0.4s
 => => transferring dockerfile: 562B                                                                                   0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                       0.0s
 => [internal] load .dockerignore                                                                                      0.2s
 => => transferring context: 2B                                                                                        0.0s
 => [1/4] FROM docker.io/library/ubuntu:latest                                                                         0.2s
 => [internal] load build context                                                                                      0.5s
 => => transferring context: 42.14kB                                                                                   0.0s
 => [2/4] RUN apt-get update && apt-get install -y     curl     wget     vim     && apt-get clean                     30.0s
 => [3/4] WORKDIR /app                                                                                                 0.5s 
 => [4/4] COPY . /app                                                                                                  0.2s 
 => exporting to image                                                                                                 1.4s 
 => => exporting layers                                                                                                1.3s 
 => => writing image sha256:0cd578be62ae3fd4896b33c85d70fb7d507525c96da7ca1346284e7dcbc89f93                           0.0s
 => => naming to docker.io/library/ubuntu-updated:latest    

 # CMD 
 CMD ["nginx", "-g", "daemon off;"]

 
 # Construir y ejecutar la imagen de Nginx


## Construir
 @Sofiaaa20 ➜ /workspaces/labs-docker-dev (main) $ docker build -t my-nginx:latest .
[+] Building 1.7s (9/9) FINISHED                                                                             docker:default
 => [internal] load build definition from Dockerfile                                                                   0.0s
 => => transferring dockerfile: 584B                                                                                   0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                       0.0s
 => [internal] load .dockerignore                                                                                      0.0s
 => => transferring context: 2B                                                                                        0.0s
 => [1/4] FROM docker.io/library/ubuntu:latest                                                                         0.0s
 => [internal] load build context                                                                                      0.1s
 => => transferring context: 18.68kB                                                                                   0.0s
 => CACHED [2/4] RUN apt-get update && apt-get install -y     curl     wget     vim     && apt-get clean               0.0s
 => CACHED [3/4] WORKDIR /app                                                                                          0.0s
 => [4/4] COPY . /app                                                                                                  0.2s
 => exporting to image                                                                                                 1.0s
 => => exporting layers                                                                                                0.9s
 => => writing image sha256:ca82a39d5d6af8c3e2c47e900d2c5330fbdebdd4cb858cc79a1c7725481920b6                           0.0s
 => => naming to docker.io/library/my-nginx:latest  


## Ejecutar 
@Sofiaaa20 ➜ /workspaces/labs-docker-dev (main) $ docker run -d -p 80:80 my-nginx:latest                                        
5fb82f85b22e66df8dad423c5e8aec69c1389df1c85e38e8bd301f0ef892c86e   