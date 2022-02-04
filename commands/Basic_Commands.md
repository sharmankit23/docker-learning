#Docker Help
$ docker

#To check the version
$ docker version

#Docker Info for config
$ docker info

#Docker Command line Structure
    #Old Way
    $ docker <commant> <option>
        #Example
        $ docker run <IMAGE>
        $ docker run -p 80:80 nginx

    #New Way
    $ docker <command> <subCommand> <option>
        #Example
        $ docker container run <IMAGE>
        $ docker container run -p 80:80 nginx

#Host to container port mapping
$ docker container run -p 80:80 nginx
$ docker container run --pubish 80:80 nginx

#Running contaner in detached mode
$ docker container run -p 80:80 -d nginx 
$ docker container run --publish 80:80 --detach --name nginx 

#Giving a user defined name to container 
$ docker container run --publish 80:80 --detach --name myContainer nginx 

#Listing all docker container
    #Running container
    $ docker container ps
    $ docker container ls 
    $ docker ps 
    $ docker ls #This will not run

    #All container
    $ docker container ls -a
    $ docker container ps -a 
    $ dcker ps -a

#Logs from container
$ docker logs <Container_Name>/<COntainer_ID>
$ docker logs myContainer
$ docker container logs myContainer