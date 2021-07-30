<p align="center"><img src="https://www.docker.com/sites/default/files/d8/2019-07/horizontal-logo-monochromatic-white.png" width="400">
</p>

## Container Description

This is a Dockerized Laravel Application built using the following containers:

- **PHP Application**

    `PHP8.0-fpm, Composer, NPM, Node.js v14.x`

- **MySQL**

    [`MySQL Official Image`](https://hub.docker.com/_/mysql/)

- **Nginx**

    [`Nginx Official Image`](https://hub.docker.com/_/nginx/)

## Getting started

#### Prerequisites:

- Docker Engine (v19.03.0+)
- Docker Compose

You can either: 
- Install [Docker Desktop](https://www.docker.com/products/docker-desktop) (includes both Docker Engine and Docker Compose)

OR

- Install [Docker Engine](https://docs.docker.com/engine/install/) and [Docker Compose](https://docs.docker.com/compose/install/) separately.

#### Setup:

1. Open a new instance of the terminal, navigate to the root directory of the project and execute the following command to bring all the containers up.
    ```
    $ docker-compose up -d
    ```
    The command will take a while to run, since it will download/build the images for the first time.
    After the images are ready, it will start the containers. 
    The next time you run this command it will be way faster to execute.
    
    *note: any change you make to the Dockerfile or any other file that the Dockerfile uses (excluding docker-compose.yaml) you will need to build the images again for the changes to take effect by executing the following command.*
    ```
    $ docker-compose build && docker-compose up -d
    ```

2. When all containers are up and running, enter the app container by executing the following command.
    ```
    $ docker-compose exec blog_app bash
    ```

3. Install all composer packages included in composer.json
    ```
    $ composer install
    ```

4. Install all npm packages included in package.json
    ```
    $ npm install
    ```

5. Run all mix tasks.
   ```
   $ npm run dev
   ```

6. Create a .env file from the existing .env.example
    ```
    $ cp .env.example .env
    ```

7. Generate a Laravel App Key.
    ```
    $ php artisan key:generate
    ```
   
8. Run the database migrations.
    ```
    $ php artisan migrate
    ```

9. Modify the following fields in your .env file to use the values specified in the database container.
    ```
    DB_CONNECTION=mysql
    DB_HOST=blog_db
    DB_PORT=3306
    DB_DATABASE=blog
    DB_USERNAME=root
    DB_PASSWORD=root
    ```

10. To access your Laravel Application visit [http://localhost:8000](http://localhost:8000)

## Watching assets for changes

If you intend to modify the assets (JS/CSS) make sure to run 
```
$ npm run watch
```
This command will continue to run in your terminal and watch relevant files for changes.

## Running Tests

To run the tests you should be inside the application container.

1. Enter the application container
    ```
    $ docker-compose exec blog_app bash
    ```

2. Run the tests
    ```
    $ vendor/bin/phpunit
    ```

## Stopping the containers

1. Exit the app container.
    ```
    $ exit
    ```

2. Bring all the containers down.
    ```
    $ docker-compose down
    ```
