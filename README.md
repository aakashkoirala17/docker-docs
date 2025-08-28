
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
git add .

#Git Branching & Conflict Resolution Guide
To create branches, push them to GitHub, merge into `main`, and resolve conflicts.

---

## Create a New Branch
A branch let us work on a feature or fix without affecting the `main` branch.

```bash
# Create and switch to a new branch
git checkout -b new-branch-name

Make Changes and Commit
After editing files, stage and commit changes:
# Stage all changes
git add .

# Commit with a message
git commit -m "Added new feature"


Push Branch to Remote

Push your local branch to GitHub:

git push -u origin new-branch-name

Switching Branches

To move between branches:
git checkout main              # Switch to main
git checkout new-branch-name   # Switch back to your branch

Merging a Branch into Main

# Go to main
git checkout main

# Pull latest updates
git pull origin main

# Merge your branch
git merge new-branch-name

Handling Merge Conflicts

If both branches edited the same lines in a file, Git cannot merge automatically.
The file will look like this:

<<<<<<< HEAD
code from main branch
=======
code from new-branch-name
>>>>>>> new-branch-name

Conflict Markers

<<<<<<< HEAD → current branch (main) changes

======= → separator

>>>>>>> new-branch-name → incoming branch changes

Remove conflict markers (<<<<<<<, =======, >>>>>>>).

Mark as resolved


git add filename
git commit

Push to main branch

git push origin main
