# Finding out exposed port of running container
	$ docker container run --detach --publish 80:80 --name proxy nginx
	# --publish HostPort:ContainerPosrt
	$ docker container port proxy
	
# Show/list network
	$ docker network ls

# Instpect network
	$ docker network inspect myNetwork

# Create a network
	$ docker network create myNetwork

# Attach a network to container 
	$ docker network connect

# Detach a network from container
	$ docker network disconnect
	
# Examples:
	# Creating a network:
	$ docker network create myNetwork
	
	# Running a container attaching the newly created network
	$ docker container run \
	--detach \
	--name proxy \
	--publish 80:80 \
	--network myNetwork \
	nginx
	
	# Attaching the network to an already running container
	$ docker container run \
	--detach \
	--name myRunningContainer \
	--publish 80:80 \
	nginx
	$ docker network connect myNetwork myRunningContainer
	
	# Inspect the container to prove that myNetwork is connected
	$ docker container inspect proxy
	
	# Inspect the network to prove that container is connected to network
	$ docker network inspect myNetwork
	
	# Disconnecting a network from a container
	$ docker network disconnect myNetwork myRunningContainer 
	
	