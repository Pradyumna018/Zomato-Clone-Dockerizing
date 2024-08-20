# Rename Your Hostname 
```
sudo hostnamectl set-hostname myapp
/bin/bash
```
# Step-1 : Create EC2 Instance and Install Dependencies
```
sudo apt-get update -y
sudo apt-get install docker.io -y
```
```
sudo usermod -aG docker $USER && newgrp docker
/bin/bash
```
```
docker --version
```
# Step-2 : Clone the Repository
```
git clone https://github.com/Pradyumna018/Zomato-Clone-Dockerizing.git
```
# Step-3 : Create a Dockerfile

The next step is to create a Dockerfile for our React application. A Dockerfile is a text file that contains instructions for building a Docker image.

In your terminal, navigate to the root directory of your React application and create a new file named `Dockerfile`.

Open the `Dockerfile` in your code editor and add the following contents:
```
# Use Node.js 16 slim as the base image
FROM node:16-slim

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the React app
RUN npm run build

# Expose port 3000 (or the port your app is configured to listen on)
EXPOSE 3000

# Start your Node.js server (assuming it serves the React app)
CMD ["npm", "start"]
```
# Step : 4 Building a Docker Image

Now that we have a Dockerfile for our Zomato application, we can build a Docker image.

In your terminal, navigate to the root directory of your Zomato application and run the following command:

```bash
docker build -t zomato-clone .
```

This command builds a Docker image with the tag `react-application` using the `.` to specify the build context as the current directory.

The build process may take a few minutes to complete, depending on the size of your application and the speed of your internet connection.

Once the build is complete, you should see a message indicating that the image was successfully built.
# Step : 5 Running the Docker Container

Now that we have a Docker image for our React application, we can run a Docker container.

In your terminal, run the following command to start a Docker container based on the image we just built:

```bash
docker run -d -p 3000:3000 zomato-clone
```

This command starts a Docker container and maps port 3000 from the container to port 3000 on your local machine. The `react-application` parameter specifies the name of the Docker image that we want to run.

With the `-d` flag, the command returns the ID of the container once it's started.

You can also use the `docker ps` command to see a list of running containers, including the ID of the container running your Zomato Clone application.

# OUTPUT

![Screenshot 2024-08-21 002650](https://github.com/user-attachments/assets/46a8c118-a082-49cd-bab4-48b19be17fa6)





