Overview:
This project demonstrates containerizing an Express Cart application using Docker and connecting it to a MongoDB database.

1. Created Dockerfile:
-> We created a Dockerfile to containerize the Express Cart application.

2. Built the Docker Image using:
-> docker build -t express-cart .

3. Created Docker Network:
-> docker network create expresscart-net

4. Set Up MongoDB Container:
-> Created a MongoDB container with persistent storage:
     docker run -d --name mongodb \
     --network expresscart-net \
     -p 27017:27017 \
     -v mongodb_data:/data/db \
     mongo:latest
5. Ran the Express Cart Container:
-> Launched the Express Cart container connected to MongoDB:
    docker run -d --name express-cart \
    --network expresscart-net \
    -p 1111:1111 \
    -e DB_HOST=mongodb \
    express-cart

After doing all the steps we can access our Application at http://localhost:1111

Some screenshots of our Application are below:
url: http://localhost:1111
 ![App Screenshot](images/Screenshot 2025-06-10 at 6.03.56 PM.png)

url: http://localhost:1111/login
 ![App Screenshot](images/Screenshot 2025-06-10 at 6.04.09 PM.png)

url: http://localhost:1111/dashboard
 ![App Screenshot](images/Screenshot 2025-06-10 at 6.04.35 PM.png)

