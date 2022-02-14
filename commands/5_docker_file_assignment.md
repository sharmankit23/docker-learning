# Problem Statement:
	1. Create an API which create user profile in mongo db & fetches list of profiles created.
	2. Create mongo db using mongo docker image
	3. Create mongo express container.
	4. Creating user_db in mongo db using mongo express
	5. API must be a container
	6. All three container must be connected by network.
	

# Solution

### Creating Network
	$ docker network create demo-app-network
	
	$ docker network ls
	
### Creating a mongo DB container
	$ docker container run \
	--detach \
	--publish 27017:27017 \
	--name dbContainer \
	--env MONGO_INITDB_ROOT_USERNAME=rootuser \
	--env MONGO_INITDB_ROOT_PASSWORD=password \
	--network demo-app-network \
	mongo
	
	$ docker container ls

### Creating mongo express container
		
	$ docker container run \
	--detach \
	--name mongoExpContainer \
	--publish 8081:8081 \
	--restart always \
	--env ME_CONFIG_MONGODB_ADMINUSERNAME=rootuser \
	--env ME_CONFIG_MONGODB_ADMINPASSWORD=password \
	--env ME_CONFIG_MONGODB_SERVER=dbContainer \
	--network demo-app-network \
	mongo-express
	
	$ docker container ls

### Creating user_db in mongo db using mongo express
	
	$ Open http://localhost:8081 & create user_db

### Creating API docker image using a docker file
		
	$ docker build -t sharmankit23/demo-api:latest .
	
### Creating API container
	
	$ docker container run \
	--detach \
	--publish 8080:8080 \
	--name appContainer \
	--network demo-app-network \
	sharmankit23/demo-api
	
	$ docker container ls
	
### Consuming the API using postman
	
	1. Create resource
		POST /user/create HTTP/1.1
		Host: localhost:8080
		Content-Type: application/json
		Cache-Control: no-cache
		Postman-Token: 6f7a92f3-1830-c53b-44b5-41d156eaf867
		
		
		{
		  "userId": "1",
		  "name" : "Mahim",
		  "userSettings" : {
		    "bike" : "Fz"
		  }
		}
		
		{
		    "userId": "1",
		    "name": "Mahim",
		    "creationDate": "2022-02-14T15:26:34.319+00:00",
		    "userSettings": {
		        "bike": "Fz"
		    }
		}
		
	2. fetch resource list
		GET /user/list HTTP/1.1
		Host: localhost:8080
		Cache-Control: no-cache
		Postman-Token: cb062b27-0e1b-c25c-abfc-a76fe6de2be9
		
		[
		    {
		        "userId": "1",
		        "name": "Mahim",
		        "creationDate": "2022-02-14T15:26:34.319+00:00",
		        "userSettings": {
		            "bike": "Fz"
		        }
		    }
		]
		
		
		