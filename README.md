# recipe-app-api
recipe api project for practice



# Some things to know
This project is built using TDD(test driven development) using the `Django test suite`, it is built into Django. to run the test use this through docker-compose:
```
docker-compose run --rm app rh -c "python manage.py test"
```

This project also uses linting with the `flake8` package. 
To use flake8 run this through docker-compose:
```
docker-compose run --rm app sh -c "flake8"
```
afte running `flake8` it is recommended to work through any errors from the bottom up. If there is no output after running `flake8` then you're good to go!

`docker-compose.yml` has:
```
args: 
    - DEV=true
```
 Keep this as is for development, but make sure to remove it for deployment.



# Before running the project, do this for setup
This project uses Docker, first make sure Docker Desktop is running.
Use: 
```
docker build .
``` 
this is the initial build for your Docker container.

After the intial docker build has run in order to build using created docker files run:
```
docker-compose build
```
Use the above for whenever any changes have been made to the docker files such as added dependencies.



# To run development server
To start docker service:
```
docker-compose up
```

To shutdown the server use `CTRL+C`


