# Stage 2 devops-django-react-task

## Description

This application consists a frontend built with react and a backend built with django.<br>
Both ends have been containerized and deployed on a cloud provider using an [ansible playbook](./stage2-server-setup-playbook.yaml)<br>
The docker images for the client and server side were built with Dockerfiles for [frontend](./frontend/Dockerfile) and [backend](./api/Dockerfile) and have been stored on docker hub and can be viewed here:
- [frontend](https://hub.docker.com/repository/docker/demarauder/hng-devops-stage2-frontend)
- [backend](https://hub.docker.com/repository/docker/demarauder/hng-devops-stage2-api)

The images are pulled and used to build up the application using the command 
```sh
docker compose up
```
to run the [docker-compose](./docker-compose.yml) file.

An NGINX reverse-proxy is set up to redirect all calls to port 80 to our frontend container port 3000.
It looks like this,
```
server{
    listen 80;
    server_name _;
    location / {
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header Host $host;

        proxy_pass http://<public IP address of frontend container on local network>:3000;

        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";

    }
}

```

A successfull result looks like this,
![home-page](https://user-images.githubusercontent.com/65220956/200078730-4378badb-45e0-4574-a49e-e7d04e90ae9a.png)

