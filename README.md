# API-CI-CD-DEPLOY-C-
A small example to apply continuous delivery and continuous integration in a .NET project. Also apply Docker containerization and implement the deployment in RENDER


# Objectives
Create a robust CI/CD workflow using Docker, GitHub Actions, and the Render platform. We will create a Docker image of the API and configure the CI/CD pipeline using GitHub Actions.
#Number of instance
In this instance, we will focus solely on creating Docker images and understanding the individual concepts of GitHub Actions. In the next instance, we will deploy using Docker Compose, integrating a MySQL database image and an API backend image.

# Big Picture of flow


![image](https://github.com/user-attachments/assets/18402582-c3af-4a5a-a627-bfa33801baf0)


# Process

1. First, create a project in ASP.NET. In my case, I will create a WEB API project. You can configure it to include a Dockerfile from the start or add the configuration later:

![image](https://github.com/user-attachments/assets/9a4e7752-5679-4c21-9e0a-22bb4222298e)

2. Create a repository on GitHub for the project.

3. Install Docker on your machine.

4. Have a Docker Hub account and Docker Desktop (OPTIONAL).

5. Sign up for Render


#Firstly we can run unit-test (Recomended)

#Running Docker Compose with the Docker Image
Open a PowerShell terminal and navigate to the root directory of the project. Execute the command docker-compose build to build your Docker image.

You can verify that the image is running:

![image](https://github.com/user-attachments/assets/a36d7486-dedf-446e-9389-0d06f4e53772)

(We could optimize the Dockerfile commands to reduce the image size, but we'll leave that for the next instance.)

#Moving the Image to Docker Hub
execute docker tag local-image:tagname ( local image) dockerhub-username/new-repo:tagname (image to be uploaded to repo)
para etiquetar nuesta imagen local de docker con un nuevo nombre y etiqueta, para subirla al docker hub

#Push to docker hub
docker push dockerhub-username/new-repo:tagname

![image](https://github.com/user-attachments/assets/a020612f-f7a6-4eea-8469-a502bedd7d8a)


#Now, pull the image from the Docker Hub repository to get the Docker image reference
docker pull dockerhub-username/new-repo:tagname

![image](https://github.com/user-attachments/assets/5f02da82-4996-4d62-a4f0-2dcb9e4662b6)


#Now we will create the service on Render

![image](https://github.com/user-attachments/assets/44ffef9e-f145-4b3e-8897-9201434375d3)


#Build PIPELINE

![image](https://github.com/user-attachments/assets/7652f3bd-eed2-4661-8225-c24fc4b2db73)


#Deploy to render automation pipeline

![image](https://github.com/user-attachments/assets/9a5b2ec3-3b22-4a90-8685-17b015935242)





