# websolutions


### Run

```
docker-compose up -d

``` 

### Inside

```
docker-compose exec wordpress bash

``` 

### Remove

```
docker-compose down --volumes
```


### Screens
  
  ![image](https://github.com/Apachy999/websolutions/blob/a418b3216d68f65d5c320999128a1b09d0fe8fdb/1.png "Screen1")
  
  ![image](https://github.com/Apachy999/websolutions/blob/a418b3216d68f65d5c320999128a1b09d0fe8fdb/2.png "Screen2")
  
---

### docker-compose.yaml

```

version: "3.7"
    
services:
  db:
    image: mysql:5.7
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: somewordpress
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress
    
  wordpress:
    depends_on:
      - db
    image: wordpress:latest
    volumes:
      - wordpress_data:/var/www/html
      - two-factor:/var/www/html/wp-content/plugins/two-factor
    ports:
      - "82:80"
    restart: always
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
      WORDPRESS_DB_NAME: wordpress
volumes:
  db_data: {}
  wordpress_data: {}
  two-factor: {}
```
  
