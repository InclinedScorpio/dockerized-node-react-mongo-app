> For Running this multi-container app in docker:

1. check if docker is running ( ```service docker status```)

2. docker network create goals-net

3. 
    Run mongo server
    ```sudo dockerun -d --network goals-net -v mongodata:/data/bin --name mongov1 -e MONGO_INITDB_ROOT_USERNAME=admin   -e MONGO_INITDB_ROOT_PASSWORD=password   mongo```

4. cd inside backend folder
    1. ```sudo docker build -t backend:v1 .```
    2. ```sudo docker run -p 80:80 --network goals-net -v $(pwd):/app -v backendlogs:/app/logs -v modulesbackend:/app/node_modules backend:v1```

4. cd inside frontend folder
    1. ```sudo docker build -t frontend:v1 .```
    2. ```sudo docker run -p 3000:3000 -v $(pwd):/app -v frontendmodule:/node_modules -it  app-frontend:v1```


***OR USE DOCKER-COMPOSE FILE***

1. check if docker is running ( ```service docker status```)

2. ```docker-compose up -d```