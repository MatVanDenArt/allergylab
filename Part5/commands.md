docker compose up
docker compose up --force-recreate

docker image ls
docker tag part5-db-loader 0abry0ec1/db-loader
docker push 0abry0ec1/db-loader

docker compose up --build

docker tag 0abry0ec1/db-loader 0abry0ec1/db-loader:v1
docker push 0abry0ec1/db-loader:v1

docker tag part5-db-loader 0abry0ec1/db-loader
docker push 0abry0ec1/db-loader