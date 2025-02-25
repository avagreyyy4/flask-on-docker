# Flask on Docker

**Overview**

In this repository I followed [TestDriven.io tutorial](https://testdriven.io/blog/dockerizing-flask-with-postgres-gunicorn-and-nginx/) tutorial which provides both a development and production setup for a Flask web application using Docker and Docker Compose. While the tutorial was slightly outdated, I was able to follow most of it with minimal changes. It includes separate configurations for development docker-compose.yml and production docker-compose.prod.yml, enabling environment management. The repository structures the Flask application within the services directory while incorporating essential configuration files for deployment and version control. This setup simplifies building, running, and deploying Flask applications in a reproducible and scalable manner using Docker. In the end, I was able to utilize these tools to upload user-media files with Nginx. 

Here is an example of me utilizing this tool to upload an image!

<img src="https://raw.githubusercontent.com/avagreyyy4/flask-on-docker/master/upload.gif" width="500">

To use these services, first, clone this repository with the command:
```
$ git clone https://github.com/avagreyyy4/flask-on-docker
```
then open it
```
$ cd flask-on-docker
```

Before moving on to the next steps, make sure docker is installed on your system.

Run the flask app in development mode:
```
$ docker-compose up -d --build
```

Now run the the Flask app in production mode:
```
$ docker-compose -f docker-compose.prod.yml up --build
```

Also, make sure to rebuild:

```
$ docker-compose down -v

$ docker-compose -f docker-compose.prod.yml up -d --build
$ docker-compose -f docker-compose.prod.yml exec web python manage.py create_db
```

You can then upload your own image at `http://localhost:1344/upload` and view it at `http://localhost:1344/media/IMAGE_FILE_NAME`
