## Steps for running Mongo with Docker
First you have to pull the image for mongo:
```bash
docker pull mongo:latest
```
In my case I already havean image: `mongo:5.0` . You can replace the `latest`  for the number you want 
(and of course is available on [Mongo release notes](https://www.mongodb.com/docs/manual/release-notes/))

Then:
```bash
docker run -d -p 27017:27017 --name=name_you_want mongo:latest
                                                  ^^^^^^^^^^^^
```

_Bear in mind that if you decided to pull another image, say mongo:5.1, you have to replace it in `mongo:latest`._

A number like this should be prompted:
```bash
d27eba610a35eb5f5649e40afccaa02d88d61b17c9a04fc6419d4a5e99ae7ca7
```

To verify it is running correctly:
```bash
docker ps
``` 

And it should return something like this:
```bash
CONTAINER ID   IMAGE       COMMAND                  CREATED          STATUS         PORTS                                           NAMES
d27eba610a35   mongo:5.0   "docker-entrypoint.s…"   11 seconds ago   Up 7 seconds   0.0.0.0:27017->27017/tcp, :::27017->27017/tcp   mongo_test
```

Now we have mongo in our computer running on port 27017 (the first port in 27017:27017) in our machine. And it is connected to port 27017 in docker container. 
It maight be confusing but remember the first port specified is for our host machine and the second is connected to the container.

We can run it on terminal with:
```bash
docker exec -it name_you_want mongo
```
And expect a result like this: (I installed 5.0)
```bash
MongoDB shell version v5.0.14
connecting to: mongodb://127.0.0.1:27017/?compressors=disabled&gssapiServiceName=mongodb
Implicit session: session { "id" : UUID("dd02a67f-2441-4fa2-98c3-b5a52ba323cb") }
MongoDB server version: 5.0.14
================
Warning: the "mongo" shell has been superseded by "mongosh",
which delivers improved usability and compatibility.The "mongo" shell has been deprecated and will be removed in
an upcoming release.
For installation instructions, see
https://docs.mongodb.com/mongodb-shell/install/
================
Welcome to the MongoDB shell.
For interactive help, type "help".
For more comprehensive documentation, see
	https://docs.mongodb.com/
Questions? Try the MongoDB Developer Community Forums
	https://community.mongodb.com
---
The server generated these startup warnings when booting: 
        2023-03-05T16:41:03.474+00:00: Using the XFS filesystem is strongly recommended with the WiredTiger storage engine. See http://dochub.mongodb.org/core/prodnotes-filesystem
        2023-03-05T16:41:05.814+00:00: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
---
---
        Enable MongoDB's free cloud-based monitoring service, which will then receive and display
        metrics about your deployment (disk utilization, CPU, operation statistics, etc).

        The monitoring data will be available on a MongoDB website with a unique URL accessible to you
        and anyone you share the URL with. MongoDB may use this information to make product
        improvements and to suggest MongoDB products and deployment options to you.

        To enable free monitoring, run the following command: db.enableFreeMonitoring()
        To permanently disable this reminder, run the following command: db.disableFreeMonitoring()
---

```

You can write `exit` to return.


Or you can use MongoDB Compass and just go to new connection and write: mongodb://localhost:27017 to connect.

Happy coding!
