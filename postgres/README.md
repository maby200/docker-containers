# Steps for running postgresql

IDK why did i use docker compose here but it works.
Once in the folder where `docker-compose.yml` is located, you can write:

```bash
docker compose up
```
it should create a container with postgresql if nothing is running on port 5432.

After that you can enter to postgresql via psql with:

Idk why it isnt asking for password. 

```bash
docker exec -it postgres_postgres_1 psql -U postgres
```
## Some useful commands:
Get list of all databases
```bash
postgres=# \l
```
 
Switch to a database:
```bash
postgres=# \c database-name
```
Show tables in that DB:


```bash
postgres=# \dt
```