# Dockerized LAMP environment

This provide a simple Docker Compose configuration for creating a LAMP environment.

## Prerequisites

Having `Docker` and `docker-compose` isntalled, as well as a local install of `composer`.

## How to use

## Webserver

1. Download any WordPress version, and place it in a `wordpress` sub-folder of the root folder (the folder where the `docker-compose.yml` file is located.
2. Open a terminal and run `docker-compose up -d`
3. Open a browser and go to `localhost:8000/wordpress/`
4. Complete WordPress 5-min install with the following database credentials:
    - **Database name**: wordpress
    - **Database user**: wordpress
    - **Database password**: wordpress
    - **Database host**: database

## Unit tests

1. Download any WordPress version, and place it in a `wordpress` sub-folder of the root folder (the folder where the `docker-compose.yml` file is located.
2. Download the matching version of [WordPress tests utilities for PHPUnit](https://github.com/WordPress/wordpress-develop/tree/master/tests/phpunit/includes), place the `includes` folder into `wordpress-tests-lib`.
3. Clone Polylang, Polylang-Pro or any third-party plugin repository inside the root folder (along the `docker-compose.yml` file.
4. For each plugin, run the `composer install` and `npm install` from your local machine.
5. Open a terminal and run `docker-compose up -d`
6. Check PHP running container's name with `docker ps`, it should look like `docker-lamp_webserver_*`.
7. Connect into the running container with `docker exec -it docker-lamp_webserver_*`.
8. Step into Polylang directory (`cd polylang`).
9. Run the test from CLI `vendor/bin/phpunit`

**/!\ Warning:** The database used will be the same than for the webserver, so all data will be reset each time the test are run!

## Removing container and data

After having run the container once, you can delete the stored databases with `docker-compose down --volumes` from the folder that contains the `docker-compose.yml` file.

