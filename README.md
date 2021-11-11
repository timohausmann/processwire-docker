# processwire-docker
My take on a docker container for processwire (or any other php+mysql project)

## Infos 

* runs on port 80
* maps docker user id to host user id, so php can write files to the host system (see `./docker-compose.yml`)
* stores mysql data in `./docker/mysql`

## Usage 

* Put latest processwire version in `./htdocs`
* Build once: `docker-compose build`
* Start container: `docker-compose up`
* Stop container: `docker-compose down`

## Database config:

```php 
$config->dbHost = 'db';
$config->dbName = 'docker';
$config->dbUser = 'docker';
$config->dbPass = 'docker';
$config->dbPort = '3306';
$config->dbCharset = 'utf8mb4'; // in case you like emojis
```