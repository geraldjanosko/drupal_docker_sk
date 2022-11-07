### Environment
Docker Compose will read docker-compose.yml and docker-compose.override.yml by default. Create a symbolic link named docker-compose.override.yml to match your environment.

In local env: ```ln -s ./docker-compose.local.yml ./docker-compose.override.yml```
In test env: ```ln -s ./docker-compose.test.yml ./docker-compose.override.yml```
In prod env: ```ln -s ./docker-compose.prod.yml ./docker-compose.override.yml```

### Database
Place a schema.sql in the db folder and it will automatically be imported to the db container post build.

### Run
run ```docker-compose up -d --build``` in the repo root.
run ```docker-compose ps``` to view the list of running containers.
run ```winpty docker exec -it CONTAINERNAME bash``` to log in to the drupal container.

### New sites
Use ```composer create-project drupal/recommended-project /app``` to create a new drupal site.

### Existing sites
Copy your composer file to the app folder and run ```composer update -w``` from inside the db container. Copy custom themes and modules folders to respective folders. Push to git.

### Shut down
run ```docker-compose down --rmi all -v``` where "--rmi all" removes images used by services and "-v" removes volumes. Remove "-v" to keep a persistent database volume.
