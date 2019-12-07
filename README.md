# Laravel boilerplate 

**Version: 6.2.\***

Requisites
- Docker
- Docker-compose

## Project configuration

First, clone the docker project:

[https://github.com/LFTroya/laravel-docker.git]

**Note:** Clone the project at the same level of your project. **Be careful**,
if you are using docker on windows. Make sure it is using **Linux containers
instead of Windows Container**, otherwise, the configuration won't work.

Second, `cd` into **laravel-docker** directory, and execute
`docker-compose up -d`. This will mount 4 containers: redis,
postgres, nginx and app. Feel free to use all of them.

After `docker-compose` finished. Make sure the configuration is OK visiting
[http://localhost:8001]. You should see the laravel home page.

Finally, configure laravel to use the configuration:

- Copy `.env.example` to `.env`
- Install dependencies `composer install`
- Generate key `php artisan key:generate`
- Update .env and setting connection to postgres

```
 DB_CONNECTION=pgsql
 DB_HOST=postgres
 DB_PORT=5432
 DB_DATABASE=postgres
 DB_USERNAME=root
 DB_PASSWORD=secret
```

That's all. You can now start developing your site!

## Things to consider:

Make sure you don't have the following ports in use: `5432`, `8001`, `80` and `6379`. 
To see if docker is using any of your ports, use `docker ps`

**Composer** is available inside of the container. If you want to access to it, you
need to enter on it. On `laravel-docker` directory, execute `docker-compose exec app bash`.
This follows the name of the services on `docker-compose` file.

**Node and npm** are also available on the container as `composer`.

**Postgres** creates an initial db to use `postgres`. The credentials
are the following: 

```
DB_HOST: postgres # Because the connection to the database will be internal on docker. Using internal dns names matching docker-compose
DB_USER: root
DB_PASSWORD: secret
DB_DATABASE: postgres
DB_DRIVER: pgsql
DB_PORT: 5432
```

**Nginx** configuration sites are available on `nginx/sites`

**Redis** credentials are:

```
DB_HOST: redis
DB_PORT: 6379
```




 
