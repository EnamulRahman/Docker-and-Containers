/ docker images         - to see images 

 

/ docker inspect 

 

/ docker rmi              -  remove images  

 

/ docker stop (CON ID)  

 

/ docker rm remove container altogether 

 

 

/ docker system prune 

 

Clean environment 

🐳 Docker Commands Cheat Sheet 

🔍 Viewing and Inspecting 

docker images 
→ Lists all Docker images on your system. 

docker inspect <container_or_image_id> 
→ Shows detailed information about a container or image (e.g., configuration, mounts, networks, etc.). 

 
 

🧹 Cleaning and Removing 

docker rmi <image_id> 
→ Removes a specific image. 
(Use -f to force remove if in use — e.g., docker rmi -f <image_id>) 

docker stop <container_id> 
→ Stops a running container. 

docker rm <container_id> 
→ Removes a stopped container. 
(Combine both: docker rm -f <container_id> to stop & remove in one go.) 

docker system prune 
→ Cleans up unused containers, networks, images, and build cache. 
(Add -a to remove all unused images, not just dangling ones — docker system prune -a) 

 
 

⚡ Useful Additions 

docker ps 
→ Lists running containers. 
(Use docker ps -a to see all containers, including stopped ones.) 

docker pull <image_name> 
→ Downloads an image from Docker Hub or a registry. 

docker run <image_name> 
→ Runs a container from an image. 
(Add -d to run in background, -p for ports, --name to name the container.) 
Example: 

docker run -d -p 8080:80 --name myapp nginx 
 

docker exec -it <container_id> bash 
→ Opens an interactive shell inside a running container. 

docker logs <container_id> 
→ Shows logs for a container. 

docker build -t <image_name> . 
→ Builds an image from a Dockerfile in the current directory. 

 
 

🧽 Quick Cleanup Combo 

docker stop $(docker ps -aq)     # Stop all containers 
docker rm $(docker ps -aq)       # Remove all containers 
docker system prune -a --volumes # Clean everything (images, cache, volumes) 

 

