# 03 - Composed Application (Dynamic)

## Requirements

- Docker (https://docs.docker.com/engine/installation/)
- Docker Compose (https://docs.docker.com/compose/)

## Installation

Be sure you are a root user. Hell ya!

```sh
curl -L https://github.com/docker/compose/releases/download/1.8.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```

## Containers

- PHP 7.x-FPM (`php:7-fpm`)
- PHP 5.6.x-FPM (`php:5.6-fpm`)
- Nginx 1.11.x (`nginx:1.11`)
- MariaDB (`mariadb`)
- Adminer (`dockette/adminer:mysql-php7`)

## Manual

1. Run `docker-compose -v` to see your docker-compose version.
2. Start connected containers with `docker-compose up`.
3. Connect to container `docker exec -it <name> bash`.
4. Go to folder `/srv` and update chmod of **var** folder. `chmod -R 0777 /srv/var`.
5. Download dependencies with `composer install`. Maybe purge `var/cache`, `var/logs`, `var/sessions`.
6. Setup database with following commands:
	- `bin/console doctrine:database:create`
	- `bin/console doctrine:schema:create`
	- `bin/console doctrine:fixtures:load`
7. Open browser.
	- PHP 7
		- `http://localhost:8000` is development version.
		- `http://localhost:8001` is production version.
	- PHP 5.6
		- `http://localhost:8010` is development version.
		- `http://localhost:8011` is production version.
	- `http://localhost:10000` occupies Adminer.

![](https://raw.githubusercontent.com/trainit/2016-docker-workshop/master/03-composed-application/misc/01.png "Composed Application!")
