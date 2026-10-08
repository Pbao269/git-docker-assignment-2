# Git and Docker Starter Application

This repository contains a small Python web application used to practice Git, GitHub, and Docker workflows.

## Application

The application listens on port 8000 and returns a text response when accessed over HTTP.

## Verification

The running application should be verified using an HTTP request to port 8000.

## Docker Usage

### Build the Application

Build the Docker image from the project directory:

    docker build -t git-docker-app:test .

### Run the Application

Start the application with host port 8080 mapped to container port 8000:

    docker run -d --name app-test -p 8080:8000 git-docker-app:test

### Verify the Application

Send an HTTP request from the host:

    curl http://localhost:8080

The response includes the developer NetID, service name, and training mode.

### View Container Logs

    docker logs app-test

### Inspect Container Configuration

    docker inspect app-test

### Stop, Restart, and Remove

    docker stop app-test
    docker start app-test
    docker rm -f app-test

### Docker Networking

Create a user-defined network:

    docker network create app-net

Run the application on the network:

    docker run -d --name app-test --network app-net git-docker-app:test

Use another container to reach the application by container name:

    docker run --rm --name network-test --network app-net curlimages/curl:8.5.0 http://app-test:8000

### Network Cleanup

    docker rm -f app-test
    docker network rm app-net
