## 🧑‍💻 Demo App – Developing with Docker

This demo app showcases a User Profile Application set up using:
- index.html with plain JavaScript and CSS for the frontend
- Node.js backend with the Express framework
- MongoDB for data storage

All components are fully containerized using Docker and can be orchestrated manually or with Docker Compose.

## 🌟 Project Highlights

Demonstrates containerization of a complete multi-tier web application
Implements Docker networking between Node.js, MongoDB, and Mongo Express
Supports both standalone Docker and Docker Compose workflows
Manages environment variables for configuration and security
Practical example for learning Docker fundamentals, environment setup, and DevOps workflows
 
## 🧰 Tech Stack & Tools
- Docker – Containerization platform
- Docker Compose – Multi-container orchestration
- Node.js & Express – Backend service
- MongoDB – Database
- ongo Express – Web-based database UI
- HTML, CSS, JavaScript – Frontend

### 🚀 Run with Docker

#### To Start the Application

Step 1: Create a Docker network

   docker network create mongo-network

Step 2: Start MongoDB

    docker run -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongodb --net mongo-network mongo    

Step 3: Start Mongo Express
    
    docker run -d -p 8081:8081 -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin -e ME_CONFIG_MONGODB_ADMINPASSWORD=password --net mongo-network --name mongo-express -e ME_CONFIG_MONGODB_SERVER=mongodb -e ME_CONFIG_MONGODB_URL=mongodb://mongodb:27017 mongo-express   

Step 4: Open Mongo Express

    http://localhost:8081

Step 5: Create a database and collection

- Database name: user-account
- Collection name: users

Step 6: Start the Node.js app

    cd app
    npm install 
    node server.js
    
Step 7: Access you nodejs application UI from browser

    http://localhost:3000

### 🧩 Run with Docker Compose

#### To start the application

Step 1: start mongodb and mongo-express

    docker-compose -f docker-compose.yaml up
    
_You can access the mongo-express under localhost:8080 from your browser_
    
Step 2: In Mongo Express, create:
  Database: user-account
  Collection: users

Step 3: Start the Node.js app     
    cd app
    npm install
    node server.js

Step 4: Access the app  
    http://localhost:3000

#### 🏗️ Build Docker Image

    docker build -t my-app:1.0 .       
    
The . refers to the folder containing your Dockerfile.
