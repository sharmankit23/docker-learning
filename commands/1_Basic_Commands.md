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

#Running container in detached mode or in background
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

#To check all the processes running inside container
	$ docker container top <Container_Id_OR_Name>
	$ docker container top myContainer

#Remove docker container from local repository
	$docker container rm <ContainerName__or_ContainerId>
	$ decker container rm myContainer
	#If Container is running then you will get error:
		$ docker container rm myContainer
			#Error response from daemon: You cannot remove a running container c9bf453f9b01d56d751fb657bc8eed71148a792e9092bf7ffce0ad5599ab1530. Stop the container before attempting removal or force remove.
	# To Remove container forcefully use -f option
	$ docker container rm -f myContainer

#Docker command help:
	#To get help on any command use --help option;
	#For example to get help on run command
	$ docker container run --help
	# To get help on rm command:
	$ docker container rm --help
	
#Start & Stop containers
	$ docker container start <ContainerName_OR_ContainerId>
	$ docker container start myCOntainer
	$ docker container stop <ContainerName_OR_ContainerId>
	$ docker container stop myContainer
	# You can give nultiple container names or ids to start or stop
		$ docker container start myContainer1 myContainer2 myContainer3
		$ docker container stop myContainer1 myContainer2 myContainer3
#Passing environmental variable to container at start time
	$ docker container run \
		--publish 8080:8080 \
		--detach \
		--name myMongoDBContainer \
		--env MONGO_INITDB_ROOT_USERNAME=rootuser \
		--env MONGO_INITDB_ROOT_PASSWORD=password \
		mongo
	# Above example is also an example of running command in multiple lines
	
	
	
	
	
	