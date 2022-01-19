# processwire-docker
My take on a docker container for processwire.

## Infos 

* maps port 80:80
* maps host userid, so docker can write to the host system (see `./docker-compose.yml`)
* volume for site: `./site`
* volume for mysql data: `./docker/mysql`

## Usage 

* `npx degit timohausmann/processwire-docker myAwesomeProject`
* Make sure your host user ID matches the user id in docker-compose.yml
* `cd myAwesomeProject`
* Build once: `docker-compose build`
* Start container: `docker-compose up`
* Visit localhost:80 and run the processwire installer
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

## File permissions:

`755` and `644` are a good place to start.
`700` and `600` should work, too.
