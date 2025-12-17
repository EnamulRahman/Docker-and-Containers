Dockerfile is series of instructions on how to build dockerimage. 

 

Allow repeatable builds 

 

5 key commands:  

 

FROM - Specifies the base image to use for the Docker image. 

 

RUN - Executes commands in the container. 

 

COPY - Copies files from the host machine into the container. 

 

WORKDIR - Sets the working directory for subsequent instructions. 

 

CMD - Specifies the command to run when the container starts. 

 
EXAMPLE: 

 

# Use the official Node.js image as the base image  

FROM node:14 

 
 

# Set the working directory in the container  

WORKDIR /app 

 
 

# Copy the package.json and package-lock.json files  

COPY package*.json ./ 

 
 

# Install dependencies 

RUN npm install 

 
 

# Copy the rest of the application code  

COPY.. 

 
 

# Expose the application port 

EXPOSE 3000 

 
 

# Specify the command to run the application  

CMD ["node", "index.js"] 

 
 

 

 
