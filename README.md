# processwire-docker

My take on a Docker container for ProcessWire.

It's using the latest ProcessWire release (master branch). 

## Usage 

* Download this repository. If you have node installed, you can use: 
`npx degit timohausmann/processwire-docker myAwesomeProject`
* In docker-compose.yml, edit the line `user: 1000:1000`: 
replace both `1000` with your host system user ID (run `id -u` to find it)
* `cd myAwesomeProject`
* Build once: `docker compose build`
* Start container: `docker compose up`
* For a new site: Visit http://localhost:8080 and run the installer 
* For an existing site: Replace the content of /site/ with your existing code and manually import a database dump.

## Database config:

```php 
$config->dbHost = 'db';
$config->dbName = 'docker';
$config->dbUser = 'docker';
$config->dbPass = 'docker';
$config->dbPort = '3306';
$config->dbCharset = 'utf8mb4';
$config->dbEngine = 'InnoDB';
```

## File permissions:

`755` and `644` are a good place to start.

`700` and `600` should work, too.
