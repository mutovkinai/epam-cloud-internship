# How to execute
### Build image from Dockerfile
NOTE to use commands u need to be in lib_catalog dir otherwise u need to chage path to Dockerfile and context

```
docker build -t backend .
```
### Create network
```
docker network create app-network
```
### Run DB container with parameters
```
docker run --name database \
           -p 5432:5432 \
           -e POSTGRES_USER=django \
           -e POSTGRES_PASSWORD=django \
           -e POSTGRES_DB=django \
           -e PGDATA=/var/lib/postgresql/data \
           -d \
           -v ${PWD}/db_data:/var/lib/postgresql/data \
           --network=app-network \
           postgres:14
```
### Run backend container
```
docker run --name backend \
           --network=app-network \
           -p 8000:8000 \
           -d \
           -it \
           backend:latest
```
# Make changes to DB schema
```
docker exec server python3 manage.py migrate
```

