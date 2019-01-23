## PHP Roadrunner Docker Image
High-performance PHP application server, load-balancer and process manager written in Golang

### Example

1) Create .rr.yml

```$xslt
http:
  address: 0.0.0.0:8080
  workers:
    command: "php public/index.php"
    pool:
      numWorkers: 1
```

2) Run docker container

```$xslt
docker run -it -p 8888:8080 -v $PROJECT_PATH:/var/www/ \ 
synortix/roadrunner:latest  -c /var/www/.rr.yml serve --debug --verbose 
```

3) You should be able to see output confirming successful server startup

```$xslt
DEBU[0000] [static]: disabled                           
DEBU[0000] [rpc]: started                               
DEBU[0000] [http]: started     
```

### Use with docker-compose

Sample docker-compose.yml
```$xslt
version: '3'

services:
  app:
    image: synortix/roadrunner:1.3-alpine
    volumes:
      - ./:/var/www
    command: " -c /var/www/.rr.yml serve --debug --verbose"
    restart: always
    ports:
      - 8888:8080

```

Refresh cache

```$xslt
docker-compose exec app roadrunner/rr -c /var/www/.rr.yml http:reset
```
