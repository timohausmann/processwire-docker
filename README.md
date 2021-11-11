# processwire-docker
My take on a docker container for processwire (or any other php+mysql project)

* runs on port 80
* maps docker user id to host user id, so php can write files to the host system (see `./docker-compose.yml`)
* stores mysql persistant in `./docker/mysql`

Put latest processwire version in `./htdocs`
Build once: `docker-compose build`
Start container: `docker-compose up`
Stop container: `docker-compose down`

database config:

```php 
$config->dbHost = 'db';
$config->dbName = 'docker';
$config->dbUser = 'docker';
$config->dbPass = 'docker';
$config->dbPort = '3306';
$config->dbCharset = 'utf8mb4'; // in case you like emojis
```