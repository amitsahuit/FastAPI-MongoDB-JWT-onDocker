# User authentication using FastAPI (a python frameworks), MongoDB (for database), Docker Compose (for deployment)
## How to start the application

**The commands:**

First you have to git clone the files by entering in your terminal:
```
$ git clone https://github.com/amitsahuit/FastAPI-MongoDB-JWT-onDocker.git
```  
Then start the application:
```
$ docker-compose up -d
```
The above command will both create the images and start the containers (2 images and 2 containers - one for the FastAPI application and one for the MongoDB database).

For visualizing the application, open up your browser and enter:

* http://127.0.0.1/docs

In the application we have seven sections:
* For authentication (the right green "Authorize" button from the above);
* For creating users (3 roles are acceptable only: "admin", "dev", "simple mortal", you'll see an error if not respecting the rule);
* For creating tokens by entering user's credentials;
* For listing the users;
* For watching the current user (only if authenticated);
* For modifying user properties (only if authenticated with admin role);
* For deleting the user.

To see the runing containers in docker, enter in the terminal:
```
$ docker ps
```
To see the database and collection created (database name is: myTestDB, collection: users) enter in your terminal:
```
$ docker exec -it <container-id> bash
```

## Configuration and file structure
Our file structure is:
```
.
├── app
│   ├── Dockerfile
│   ├── __init__.py
│   ├── main.py
│   ├── requirements.txt
│   └── src
│       ├── __init__.py
│       ├── dependecies.py
│       ├── models.py
│       ├── routers.py
│       └── settings.py
└── docker-compose.yml
```
In the app directory in ```main.py``` file we make all the dependencies and routers importing from the same name files located in ```src``` directory.

```src``` directory is the one that containes all the needed pydantic models (models.py), database and authentication variables (settings.py). 

Authentication is made by using ```bearer``` scheme with ```token``` creation and usage.

```dependecies.py``` is the file containing authentication fucntions (I also made an authentication middleware located in ```main.py``` file in the root directory using ```basic``` scheme, this function serves as an example purpose only).
