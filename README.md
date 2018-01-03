# Admin
Simple admin skeleton with Symfony 4

## Getting started
These instructions will get you a copy of the project environment up and running on your local machine for development and testing purposes.

### Prerequisites
You must have installed [docker](https://docs.docker.com/engine/installation/) (17.06+) and [docker-compose](https://docs.docker.com/compose/install/) (1.13+) on your local machine to run it easily.

### Installing
1. Clone repo.

2. Copy `.env.dist` to `.env` and edit as needed with your favorite text editor (i.e. nano .env)

### Usage

```bash
docker-compose up -d
```
### Configuring a Web Server to run Symfony 4


```bash
docker exec -ti admin_php-apache_1 sh -c "sed -i -- 's/DocumentRoot \/var\/www\/html/DocumentRoot \/var\/www\/html\/public/g' /etc/apache2/sites-available/default-ssl.conf && sed -i -- 's/DocumentRoot \/var\/www\/html/DocumentRoot \/var\/www\/html\/public/g' /etc/apache2/sites-available/000-default.conf && sed -i -- 's/<Directory \/var\/www\/html\/>/<Directory \/var\/www\/html\/public\/>/g' /etc/apache2/apache2.conf"
```
### Enable pdo and pdo_mysql extensions
```bash
docker exec -ti admin_php-apache_1 docker-php-ext-install pdo pdo_mysql

```

### Install new packages via composer

```bash
docker run --rm --interactive --tty --volume $PWD:/app --user $(id -u):$(id -g) composer require PACKAGE_NAME
```

### Another useful Docker commands

```bash
# List containers
docker-compose ps

# View logs
docker-compose logs

# Start containers
docker-compose start

# Restart containers
docker-compose restart

# Stop containers
docker-compose stop

# Stop and remove containers.
docker-compose down
```

### Project created with Symfony official skeleton

```bash
docker run --rm --interactive --tty --volume $PWD:/app --user $(id -u):$(id -g) composer create-project symfony/skeleton admin
```