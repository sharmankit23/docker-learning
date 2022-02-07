#Logs from container
	$ docker logs <Container_Name>/<COntainer_ID>
	$ docker logs myContainer
	$ docker container logs myContainer

#To check all the processes running inside container
	$ docker container top <Container_Id_OR_Name>
	$ docker container top myContainer

# Data or meta data about the container
	$ docker container inspect myCOntainer
	
# Checking the stats for a container:
	$ docker container stats myDBContainer
	
# Starting a new container interactively
	$ docker container run -it --name proxy nginx bash
	$ docker container start -ai proxy

# Taking control of an already running container
	$ docker container run --detach --name proxy nginx
	$ docker container exec -it proxy bash
