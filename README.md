## Detail logger app - Developed with Docker

This detail logger app shows a simple user profile app set up using 
- index.html with pure JS and CSS styles
- NodeJS backend with Express module
- MongoDB for data storage

All components are docker-based

Frontend looks something like this -

![front](https://github.com/rakshaa-01/detail-logger-app-docker/assets/97796804/530a8f05-8de4-4cd3-b23d-afc166e2cea4)


### With Docker

#### To start the application

Step 1: Create docker network

    docker network create mongo-network 

Step 2: Start mongodb 

    docker run -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongodb --net mongo-network mongo    

Step 3: Start mongo-express
    
    docker run -d -p 8081:8081 -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin -e ME_CONFIG_MONGODB_ADMINPASSWORD=password --net mongo-network --name mongo-express -e ME_CONFIG_MONGODB_SERVER=mongodb mongo-express   

_(Creating docker network is optional)

Step 4: Open mongo-express from browser

    http://localhost:8081

Step 5: Create `user-account` _db_ and `users` _collection_ in mongo-express

Step 6: Start your nodejs application locally - go to `app` directory of project 

    npm install 
    node server.js
    
Step 7: Access you nodejs application UI from browser

    http://localhost:3000

### With Docker Compose

#### To start the application

Step 1: Start mongodb and mongo-express

    docker-compose -f docker-compose.yaml up
    
_Access the mongo-express under localhost:8081 from your browser_
    
Step 2: In mongo-express UI - create a new database "my-db"

Step 3: In mongo-express UI - create a new collection "users" in the database "my-db"       
    
Step 4: Start node server 

    npm install
    node server.js
    
Step 5: Access the nodejs application from browser 

    http://localhost:3000

#### To build a docker image from the application

    docker build -t my-app:1.0 .       
    
The dot "." at the end of the command denotes location of the Dockerfile. '.' indicates the current location.
