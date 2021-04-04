# Symfony Docker Boilerplate

## Create symfony app

Enter php container and create symfony app in the current directory.

``` 
docker exec -it php-container bash 

composer create-project symfony/skeleton .
```

Now if you run: `docker-compose up -d --build` and navigate to `localhost:8080` you will be presented with the symfony welcome page.

## Connecting to the mysql db

Edit the `.env` file located inside you symfony app folder. Change the `DATABASE_URL` to your database connection string. Here is an example:

```
DATABASE_URL="mysql://<db-username>:<db-password>@mysql-container:3306/<db-name>?serverVersion=8"
```

## Using doctrine [Optional]

Add doctrine ORM to your symfony project.

``` 
docker exec -it php-container bash 

composer require doctrine
```
Create the database using the `doctrine:database:create` command.
```
docker-compose run --rm php-service php bin/console doctrine:database:create
```

## Symfony Encore [Optional]

Webpack setup with Symfony Encore.

```
docker exec -it php-container bash

composer require encore
```

Install the npm packages using node.

```
docker-compose run --rm node-service yarn install
```

Compile files with webpack

```
docker-compose run --rm node-service yarn dev
```
