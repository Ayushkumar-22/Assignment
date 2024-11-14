# Assignment


Containerized Full-Stack Application Deployment with Docker
This project demonstrates how to deploy a containerized full-stack application locally using Docker, making it simple to manage and scale each component of the stack. The application includes a React frontend, Express backend, and MongoDB database, all coordinated through Docker Compose for efficient orchestration. A convenient shell script further automates the build, push, and deployment processes, reducing manual work and ensuring a smooth deployment experience.

Special Thanks: This project was made possible through the valuable guidance and support provided by mentors and contributors who shared their expertise in containerization and full-stack development. Their insights have been instrumental in shaping the project’s architecture and ensuring best practices throughout.

Project Overview
Frontend Dockerfile: Defines how to build and serve the React frontend within a Docker container.
Backend Dockerfile: Defines the configuration for running the Express backend in a container.
Docker Compose: Manages the orchestration and networking of frontend, backend, and MongoDB containers.
Deployment Script: Automates Docker build, push, and run commands for efficient deployment.
Table of Contents
Getting Started
Docker Configuration Files
Frontend Dockerfile
Backend Dockerfile
Docker Compose File
Deployment Script
Running the Application
Access and Testing
Troubleshooting and Maintenance
Getting Started
To deploy this application on your local machine, ensure you have the following:

Docker: Install Docker on your operating system.
Docker Hub Account (optional): Required if you plan to push images to Docker Hub for public or collaborative access.
First, clone the repository and navigate to the project’s root directory:

git clone https://github.com/Ayushkumar-22/Assignment.git
cd Assignment-Submission-Repo-
Docker Configuration Files
1. Frontend Dockerfile
The frontend Dockerfile sets up the React application to build and run in a containerized environment:

Uses a Node.js base image to build the frontend.
Copies relevant project files into the container.
Installs dependencies and builds the production-ready frontend.
Serves the built frontend using a lightweight web server for optimal performance.
2. Backend Dockerfile
The backend Dockerfile provides the necessary configuration for the Express server:

Uses a Node.js base image.
Copies backend files into the container.
Installs backend dependencies.
Exposes the required port and initiates the server.
3. Docker Compose File
The docker-compose.yml file orchestrates the deployment of the full-stack application by coordinating three services:

Frontend: Builds the React frontend image and maps it to port 3000.
Backend: Builds the Express backend image and maps it to port 5000.
MongoDB: Pulls the official MongoDB image and maps it to port 27017, providing database connectivity.
4. Deployment Script
The shell script (deploy.sh) automates core Docker tasks:

Builds and tags Docker images for both frontend and backend.
Pushes these images to Docker Hub if specified in the script.
Launches Docker Compose to start the entire application.
Make the script executable by running:

chmod +x deploy.sh
To execute the script:

./deploy.sh
This will handle the build, push (if Docker Hub is configured), and deployment in one step, saving time and simplifying deployment.

Running the Application
Option 1: Using Docker Compose
Build and start the services:

docker-compose up --build -d
This command will:

Build Docker images for both the frontend and backend.
Launch containers for each service, including MongoDB.
Configure networking between containers to ensure smooth inter-service communication.
Stop the services:

docker-compose down
Option 2: Using the Deployment Script
You can also use the deploy.sh script to automate the build, push, and deployment steps:

./deploy.sh
This script will:

Build images for the frontend and backend, pushing to Docker Hub if configured.
Run docker-compose up to start all services.
Note: If using Docker Hub, ensure your credentials are set up in the script or in your Docker configuration.

Access and Testing
Once the application is up and running, access each component via the following URLs:

Frontend: http://localhost:3000 — Access the React frontend interface.
Backend: http://localhost:5000 — Connect to the Express backend API.
API Endpoint: http://localhost:5000/api/users — Test the /api/users endpoint for data access and API functionality.
Troubleshooting and Maintenance
Common Issues
"Cannot GET /" Error: This typically occurs if the backend root URL is undefined. Ensure your API requests use the appropriate endpoints (e.g., /api/users).
MongoDB Connectivity Errors: Verify that the MongoDB container is running and accessible. The MONGO_URI environment variable should reference the MongoDB container correctly.
Rebuilding the Application
If you modify any code and need to see changes in the containerized app, you’ll need to rebuild:

docker-compose up --build -d
This command will refresh your images with the latest code changes and redeploy the application.

With this setup, deploying a full-stack application becomes manageable and efficient, providing a robust local development environment that closely mimics production. The combination of Docker, Docker Compose, and a deployment script offers a streamlined, scalable solution for modern web applications.

Acknowledgments: A heartfelt thanks to all contributors and mentors whose knowledge and guidance have been invaluable in developing this project. Their support has greatly enhanced the quality of this deployment process, ensuring both best practices and reliability.
