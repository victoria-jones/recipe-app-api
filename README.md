# recipe-app-api
recipe api project for practice



# Some things to know
This project is built using TDD(test driven development) using the `Django test suite`, it is built into Django. to run the test use this through docker-compose:
```
docker-compose run --rm app sh -c "python manage.py test"
```

This project also uses linting with the `flake8` package.
To use flake8 run this through docker-compose:
```
docker-compose run --rm app sh -c "flake8"
```
afte running `flake8` it is recommended to work through any errors from the bottom up. If there is no output after running `flake8` then you're good to go!

This project runs tests and linting through `Github Actions` so you shouldn't need to do any of this manually. The `Github Actions` run each time code is commited to github, to see the results of the tests and linting go to `Github Actions` tab. You can still run either of these manually if you want before making a commit, just use the above code.

`docker-compose.yml` has:
```
args:
    - DEV=true
```
 Keep this as is for development, but make sure to remove it for deployment.

 ## wait_for_db
 Sometimes when firing up docker or running commands docker will have the app up and ready to go before the database. To fix any errors from this there is a file `wait_for_db.py` that can be run before doing anything with the app. Here's an example of how to use it:
 ```
 docker-compose run --rm app sh -c "python manage.py wait_for_db && python manage.py migrate"
 ```
In this example we make sure the database is running and connected before trying to make a migration


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
sometimes you need to clear the container too and you can do that by running:
```
docker-compose down
```


# Tests
Keep tests inside the `test` folder. All tests must be prefixed with `test_`. When writing a test you will need to import this for a basic test:
```
from django.test import SimpleTestCase
```
When writing a test for the database you will use:
```
from django.test import TestCase
```

# The Database
This project uses PostgreSQL. Everything is configured and defined in docker. The network connectivity is through docker services.

## Test Database
This project uses a specific database for testing. Every time a test is run the database is wiped clean (this happens by default).
