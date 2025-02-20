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



