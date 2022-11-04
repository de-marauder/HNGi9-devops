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

## Backend development workflow

```sh
virtualenv env
source env/bin/activate
pip install -r requirements.txt
python manage.py runserver
```

## Frontend development workflow

You are to update your name in ./frontend/components/App.js

```json
npm i
npm start
```

## For deploying

```json
npm run build
```

It should look like this if successful
<img width="1440" alt="Screen Shot 2022-11-02 at 19 30 22" src="https://user-images.githubusercontent.com/66765302/199572589-43bd05b7-95a6-455c-bc25-3cd437c95339.png">
