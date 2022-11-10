### Environment
Docker Compose will read docker-compose.yml and docker-compose.override.yml by default. Create a symbolic link named docker-compose.override.yml to match your environment.

In local env: ```ln -s ./docker-compose.local.yml ./docker-compose.override.yml```
In test env: ```ln -s ./docker-compose.test.yml ./docker-compose.override.yml```
In prod env: ```ln -s ./docker-compose.prod.yml ./docker-compose.override.yml```

### Database
Place a schema.sql in the db folder and it will automatically be imported to the db container post build.

### Copy the starter kit
run ```cp -r drupal_docker_sk SITENAME``` to copy the starter kit to a new site.
run ```cd SITENAME && rm -rf .git``` to navigate to your new site and remove the starter kit git repository.
run ```git init && git remote add origin SSHGITREPO``` to connect your new site to a git repository.

### Start docker
run ```docker-compose up -d --build``` in the site root to build the docker volumes, images and containers.
run ```docker-compose ps``` to view the list of running containers.

## Bash
run ```winpty docker exec -it CONTAINERNAME bash``` to enter the drupal/database containers. Once inside the container you can run the commands available to that container.

### Composer
Use the provided composer.json file or copy your existing sites composer file to the app folder and run ```composer update -w```.

### Drush
Use ```composer require --dev drush/drush``` to install the latest version of drush.

### Shut down
If you are current inside the container run the ```exit``` command.
run ```docker-compose down --rmi all -v``` where "--rmi all" removes images used by services and "-v" removes volumes. Remove "-v" to keep a persistent database volume.
