# Overview
This repo uses a PostgreSQL with Flask application for development. It leverages Nginx as a web load balancer, Flask with Gunicorn for the web framework, and PostgreSQL for reliable data storage. The infrastructure is containerized using Docker. It also has separate development and production environments for deployment.

## Build
1. First, check if Docker and Docker Compose are installed
2. Clone this repo:
```
https://github.com/nicholaslasko123/flask-on-docker-4
cd flask-on-docker-4
```
3. Build the images and run the containers:
```
$ docker compose up -d --build
```
 This uses the docker-compose.yml file to create images.

4. Bring down services, build images, and spin containers:
```
$ docker compose down -v
$ docker compose -f docker-compose.prod.yml up -d --build
$ docker compose -f docker-compose.prod.yml exec web python manage.py create_db
```

We are moving into the production stage in which we prepare for users. We use docker-compose.prod.yml to build the image. This includes a .env.dev file that integrates Gunicorn and Nginx to enhance performance and scalability.

Access a port on a Firefox browser:
```
http://localhost:5009/upload
```
Click the browse button and pick the Happy Birthday GIF image.
You should be able to see the image at 
```      
http://localhost:5009/media/Happy_Birthday_GIF.gif
```
You can set up port forwarding to map port 5009 to another port. This allows you to connect through your browser using the reassigned port.

https://github.com/user-attachments/assets/bb409464-5bcf-40c1-a273-221d9dfb1c33

