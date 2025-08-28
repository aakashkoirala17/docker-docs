
# docker-docs

installing docker

creating docker images

creating a folder for Dockerfile

creating nano Dockerfile

#creating a python app hello.py

from flask import Flask
app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello World!"

The following Dockerfile creates a container image, which has all the dependencies installed and that automatically starts your application.


# syntax=docker/dockerfile:1
FROM ubuntu:22.04

# install app dependencies
RUN apt-get update && apt-get install -y python3 python3-pip
RUN pip install flask==3.0.*

# install app
COPY hello.py /

# final configuration
ENV FLASK_APP=hello
EXPOSE 8000
CMD ["flask", "run", "--host", "0.0.0.0", "--port", "8000"]



docker build -t myapp:1

docker run --rm myapp:1

docker run -p 127.0.0.1:8000:8000 myapp:1


# docker-docs
this is anoter branch craeted

 another-branch
