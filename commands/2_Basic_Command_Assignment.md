# Problem Statement
## (A). Create three containers with below mentioned Config:
### 1. nGinx:
		Port Mappings: 80-->80
		Container Name: myProxyContainer
		Detached: Yes
		
### 2. httpd
		Port Mapping: 8080-->8080
		Container Name: myServerContainer
		Detached: Yes
### 3. mongobd
		Port Mapping: 8081-->27017
		User: rootuser
		PDW: password
		Detached: yes
		Name: myDBContainer
		
## (B). Print startup logs for mongo db

## (C). Stop Containers

## (D). Remove containers

# Solution
##Commands:
### nginx
	$ docker container run --detach --publish 80:80 --name myProxyContainer nginx
### httpd
	$ docker container run --detach --publish 8080:80 --name myServerContainer httpd
### mongo
	$ docker container run \
	--detach \
	--publish 8081:27017 \
	--name myDBContainer \
	--env MONGO_INITDB_ROOT_USERNAME=rootuser \
	--env MONGO_INITDB_ROOT_PASSWORD=password \
	mongo
### Docker container check
	$ docker container ls
### Printing startup logs for mongo db
	$ docker container logs myDBContainer
### Stop all containers
	$ docker container stop myDBContainer myServerContainer myProxyContainer
### Remove all containers
	$ docker container rm myDBContainer myServerContainer myProxyContainer
		

		
		