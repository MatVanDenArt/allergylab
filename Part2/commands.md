
docker pull quanticschoolofbusiness/103mysql
docker images
docker build -t pythonapp:latest .
docker network create python-app-network
docker network ls
docker run --name dbhost -d --network=python-app-network quanticschoolofbusiness/103mysql
docker run --name app -d -p 3006:3006 --network=python-app-network pythonapp
docker ps
docker stop app
docker stop dbhost