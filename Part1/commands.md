docker build -t my-first-app:latest .
docker run --name container_1 -d -p 3006:3006 my-first-app
docker ps
docker stop container_1
docker rm container_1