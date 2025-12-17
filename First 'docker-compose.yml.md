.yml file is a recipe that has everything the application needs 

 

version: '3.8' 
 
 

services: 
 

  web: 
    build: . 
   

  ports: 
      - "5000:5000" 
 

    depends_on: 
      - db 
 

 

 
  db: 
   

  image: mysql:5.7 
 

    environment: 
 

      MYSQL_ROOT_PASSWORD: my-secret-pw 

 

 

version: '3.8' → Defines the Docker Compose file format version (3.8 supports modern Compose features). 

services: → Lists all containers that will run in this application. 

 
 

🌐 Service: web 

build: . → 

Builds the Docker image using the Dockerfile in the current directory (.). 

ports: 

"5000:5000" → Maps host port 5000 to container port 5000, so you can access the app via localhost:5000. 

depends_on: 

- db → Ensures the web service starts after the db (MySQL) service is up. 

 
 

🗄️ Service: db 

image: mysql:8 → Uses the official MySQL version 8 image from Docker Hub. 

environment: 

MYSQL_ROOT_PASSWORD: my-secret-pw → Sets the root password for MySQL. 

 

 

 

/ docker compose up –d (background) 

 

 

To stop containers docker compose down 

 
