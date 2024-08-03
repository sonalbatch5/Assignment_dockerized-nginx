# Dockerized Nginx Web Server

## Objective

This project demonstrates how to Dockerize a simple HTML page using Nginx as the web server.

## Files

### index.html

This is a plain HTML file with the content "Hello World!".

### nginx.conf

This is the Nginx configuration file. It configures Nginx to listen on port 80 and serve the `index.html` file.

### Dockerfile

This file defines the Docker image:

- It uses the official Nginx base image.
- It copies the `nginx.conf` and `index.html` files into the appropriate locations in the container.
- It exposes port 80.
- It starts the Nginx server when the container is run.

### Docker-compose.yml

This file builds and runs the container using Docker Compose

## Steps to Build and Run the Docker Container:

 **Using Docker:**
1. **Build the Docker image:**

        docker build -t my-nginx-image .

2. **Run the Docker container:**

        docker run -d -p 80:80 my-nginx-image

Access the webpage by navigating to http://localhost in your web browser.

**Using Docker Compose:**

   **Build and run the Docker container:**

    docker-compose up --build -d


Access the webpage by navigating to http://localhost in your web browser

## Steps to Push the Docker Image to Amazon ECR

1. **Authenticate Docker to Your ECR Registry:**
   
       aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/f8g8h5d4

2. **Build and Tag Your Image:**

       docker build -t sonal_dockerizing-html .

       docker tag sonal_dockerizing-html:latest public.ecr.aws/f8g8h5d4/sonal_dockerizing-html:latest


3. **Push your Docker image to the ECR repository:**

       docker push public.ecr.aws/f8g8h5d4/sonal_dockerizing-html:latest

**Public ECR Repository:**

   You can find the public ECR repository at the following link: public.ecr.aws/f8g8h5d4/sonal-repo:latest



