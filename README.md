# lab10Devop-1


services:
  mysql:
    image: mysql:latest
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
    ports:
      - "3307:3306"
    volumes:
      - mysql_data:/var/lib/mysql

  phpmyadmin:
    image: phpmyadmin:latest
    depends_on:
      - mysql
    environment:
      PMA_HOST: mysql
      PMA_USER: root
      PMA_PASSWORD: rootpassword
    ports:
      - "9000:80"

volumes:
  mysql_data:



docker compose up -d

docker compose down

docker compose up -d / docker volume ls / docker volume rm {name}



//2.1

services:
  web:
    image: kengchayodom/test
    ports:
      - "8105:80"

docker compose up -d

//2.2
docker build -t kengchayodom/test:3.0 .
docker push kengchayodom/test:3.0


docker pull kengchayodom/test:3.0
docker run -p 8106:80 kengchayodom/test:3.0

2.3
docker pull kengchayodom/test:4.0
docker run -p 8108:80 kengchayodom/test:4.0

2.4 window shell
docker buildx create --use --name mybuilder / docker buildx inspect --bootstrap

2.5
docker buildx build --platform linux/amd64,linux/arm64 -t kengchayodom/myimage:latest .

2.6
docker buildx build --platform linux/amd64,linux/arm64 -t kengchayodom/myimage:latest --push .

https://hub.docker.com/repository/docker/kengchayodom/myimage/tags


3.

touch docker-compose.yml

vi docker-compose.yml

insert : 
version: '3.8'
services:
  mongo:
    image: mongo:latest
    container_name: mongo_db
    restart: always
    ports:
      - "27017:27017"
    environment:
      MONGO_INITDB_ROOT_USERNAME: admin
      MONGO_INITDB_ROOT_PASSWORD: password
    volumes:
      - mongo_data:/data/db

  mongo-express:
    image: mongo-express:latest
    container_name: mongo_express
    restart: always
    ports:
      - "8081:8081"
    environment:
      ME_CONFIG_MONGODB_ADMINUSERNAME: admin
      ME_CONFIG_MONGODB_ADMINPASSWORD: password
      ME_CONFIG_MONGODB_SERVER: mongo

volumes:
  mongo_data:



cat docker-compose.yml

docker-compose up -d

see on 8081 port
