# Hello Service — Docker, Kubernetes & Jenkins practice

Small Spring Boot application using Java 21.

## 1. Run locally first
Open CMD/PowerShell in this folder and run:

    mvn spring-boot:run

Open http://localhost:8085/hello. Expected response:
`Hello from Docker and Kubernetes learning!`

Stop with Ctrl+C.

## 2. Build the JAR

    mvn clean package

## 3. Build and run with Docker Desktop

    docker build -t hello-service:1.0 .
    docker run --name hello-service -p 8085:8085 hello-service:1.0

Open http://localhost:8085/hello.

Java 21 and Maven are required for local build/run. Docker Desktop must be running for Docker commands. Port 8085 avoids conflict with the Northstar API Gateway on 8080. Start with local run first; add Kubernetes and Jenkins after this works.
