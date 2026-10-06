[![Development Build](https://github.com/lumorgan321Mudd/flask-on-docker/actions/workflows/main.yml/badge.svg?branch=main)](https://github.com/lumorgan321Mudd/flask-on-docker/actions/workflows/main.yml)

Overview:
This repository contains a Flask web application with separate production and development environments that run on Docker with Postgres. The development environment is used for quick testing while the production environment is for more reliable real world use and avoids automatically resetting important data. In production, the flask application is served through Gunicorn, while Nginx acts as a reverse proxy in front of it serving static and media files directly. The project also uses docker volumes to store things like Postgres data, static files, and uploaded media so that when a container is deleted these things are preserved. This project is a flask application that uses Docker to manage services and deployment.

Build Instructions:
Docker is required to run the application. Clone the repository and navigate inside the repository directory before running the commands below. The .env files are not included in the repository for security reasons and must be provided separately.

Development:
For development build and start the services with the command: docker compose up -d --build. Then you can access the webpage using the following url: http://localhost:1140. To stop the services run the command: docker compose down.

Production:
For production build and start the services with the command: docker compose -f docker-compose.prod.yml up -d --build. If the database has not been initialized yet run the command: docker compose -f docker-compose.prod.yml exec web python manage.py create_db. Then you can open the webpage with the following url: http://localhost:1140. To upload an image, go to the url: http://localhost:1140/upload. Choose a file a hit upload. You can view the image at the url: http://localhost:1140/media/FILE_NAME. You can also access static files in the application with the url: http://localhost:1140/static/FILE_NAME.
