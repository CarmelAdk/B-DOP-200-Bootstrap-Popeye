# B2 - Introduction to DevOps
##  Popeye - Bootstrap 


### STEP 0 - HELLO DOCKER!
#### A LITTLE QUIZ TO START WITH
- What is Docker?  
    ```Docker``` is a platform designed to help for building, sharing, testing and running modern applications. It uses OS-level virtualization to deliver software in packages called containers.
- What is the difference between Virtual Machines and Docker containers?
    1. VM's have their own entire OS while multiple ```Docker``` containers can be hosted by a single OS.
    2. VM’s may take several minutes to boot up their OS and finally run the required apps while containerized applications can be started almost instantly.
    3. For VM's, there are limitations in case of platform support for applications, shipping, scalability while ```Docker``` containers supports multiple platforms, easily shippable and scalable.
- How much are 2 Docker containers separated when running on the same machine?  
    There are totally separated : process, filesystem, network, resource, etc. However, ```Docker``` containers can interact with each other through shared volumes, network connections.
- What is the difference between a Docker container and a Docker image?  
    I don't know if I can use the analogy of class and object in Object-oriented Programming(OOP). A ```Docker``` image is a read-only immutable template that defines how a container will be realized. A ```Docker``` container is a runtime instance of a ```Docker``` image. It is created when the docker run command is executed.
- In what way will spinach helps you to master DevOps?

    ```
    This is like spinaches for programmers: at first, it feels strange and does not taste good, 
    but in the end, you become an incredibly strong sailor that loves those tools and is a master at using them.
    ``` 
    Yes, Yes, I copied the quote but it answers the question quite well, I guess.

#### SETUP TIME
1. Installation of Docker, Docker Compose. I wrote a Notion on it. Maybe, I will publish it. Maybe not.  
2. Installation of PostgreSQL client. I chose the command-line tool (postgresql).  
    - Update the package index and install the package.
    > cli
    ```bash
    sudo apt update  
    sudo apt install postgre-sql 
    ```
    - Check if installation is successful.
    > cli
    ```bash
    psql --version
    ```
    > Output 
    ```bash
    psql (PostgreSQL) 12.14 (Ubuntu 12.14-0ubuntu0.20.04.1)      
    ```
    

#### HANDS ON THE RUDDER
1. Find the official PostgreSQL image and import it on my machine.  
    I went to [Docker hub](https://hub.docker.com/search) and searched for postgresql. I found the official image : ```postgres```.  
    There is also a command-line way to find the official image :
    > cli
    ```bash
    docker search postgresql --filter=is-official=true
    ```
    > Output 
    ```bash
    NAME       DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
    postgres   The PostgreSQL object-relational database sy…   12148     [OK]       
    ```
    For the import :
    ```bash
    docker pull postgres
    ```
2. Show how many images I have on my machine.
    > cli 

    ```bash
    docker images|awk '{print $1}' |grep '^[a-z]' |wc -l
    ```
    > Output
    ```bash
    7
    ```
3. Run a PostgreSQL container.
    ```bash
    docker run --name="postgres" -d postgres
    ```
4. Show containers running on my machine. 
    > cli
    ```bash
    docker ps
    ```
    > Output 
    ```bash
    CONTAINER ID   IMAGE      COMMAND                  CREATED         STATUS         PORTS      NAMES
    c9a2fa12d115   postgres   "docker-entrypoint.s…"   5 minutes ago   Up 5 minutes   5432/tcp   postgres
    ```
    Yes, I see the container ID of PostgreSQl (obvious!).
5. Is my previous PostgreSQL container still running?
   Yes it did. I'll stop it.
    > cli
    ```bash
    docker stop c9a2fa12d115
    ```
6. Remove the container.
    > cli
    ```bash
    docker rm c9a2fa12d115
    ```
7. Run a container with PostgreSQL 9.4 version.
    > cli
    ```bash
    docker run -d postgres:9.4
    ```
8. Make the needed port is exposed on my machine.  
    The official Docker image for PostgreSQL uses the default port 5432 for communication between clients and the PostgreSQL server.
    When I tried to connect myself to the server :
    > cli
    ```bash
    psql "postgres://postgres:postgres@localhost:5432/postgres"
    ```  
    > Output 
    ```bash
    psql: error: could not connect to server: Connexion refusée
	Is the server running on host "localhost" (127.0.0.1) and accepting
	TCP/IP connections on port 5432?
    ```  
    Let's fix it.  
    I chose the port 5432 on my machine in order to map it to the port 5432 of the container.
    ```bash
    docker run --name="postgres" -p 5432:5432 -d postgres
    ```
    Now, when I retry... 
    > Output 
    ```bash

    ```  

9. Change PostgreSQL’s password (when executing docker run).
    ```bash
    docker run --name="postgres" -e POSTGRES_PASSWORD=psw -d postgres
    ```
10. 
11. Find out which day it is in the container.
    > cli
    ```bash
    
    ```
    > Output 
    ```bash
    ```
12. Display the logs of my container.

    To display in real time.


### STEP 1 - TIME TO CRAFT
- I wrote the [Dockerfile](app/Dockerfile) which respects the specifications given.
- I built my image.
    > cli
    ```bash
        docker build -t mynodeapppopeyebootstrap app
    ```
- I launched my container
    > cli
    ```bash
        docker run --name popeyebtcontainer -p 85:3000 -d mynodeapppopeyebootstrap
    ```
### STEP 2 - TIME TO CRAFT THE CRAFTER
