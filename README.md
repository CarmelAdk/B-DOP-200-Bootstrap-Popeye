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
Installation of Docker, Docker Compose. I wrote a Notion on it. Maybe, I will make it public. Maybe not.  
Installation of PostgreSQL client. I chose the command-line tool (postgresql).

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
    docker run -it postgres /bin/bash
    ```
4. Show containers running on my machine. 
    > cli
    ```bash
    docker ps
    ```
     Output
    Yes, I see the container ID of PostgreSQl Obvious.
5. Is my previous PostgreSQL container still running?
   Yes it did. Ill stop it.
    > cli
    ```bash
    docker stop 
    ```
6. Remove the container.
    > cli
    ```bash
    docker rm 
    ```
7. Run a container with PostgreSQL 9.4 version.
    > cli
    ```bash
    docker run postgres9.4
    ```
8. 


### STEP 1 - TIME TO CRAFT
### STEP 2 - TIME TO CRAFT THE CRAFTER
