# Install Twasi-Core using Docker

Using docker is the easiest way to install Twasi-Core. It will run on all systems.

First, install docker on your system. You can find a tutorial about this [here](https://docs.docker.com/engine/installation).

Next, you need to start an instance of MongoDB. We recommend to have the volume on the host system (this makes it easier for upgrades).

```
sudo docker run -d -p 27017:27017 -v /home/twasi/beta/db:/data/db mongo mongod
```
This command downloads and runs MongoDB. It mapps the hostport 27017 to the guest port 27017 and the guest directory (volume) /data/db to the host directory /home/twasi/beta/db. -d signals to detach (run in background).

After that, your MongoDB Server should run and be accessible on port 27017 of the host.

Next we need to enable authentication. For this, install mongodb-clients first:

```
sudo apt-get install mongodb-clients
```

Then we are able to connect to our database:

```
mongo localhost/admin
```

Admin is a default mongodb database in which the global users are stored. We need to create an admin user now.

```javascript
db.createUser({user: "root", pwd: "s3cur3p4ssw0rd", roles:["root"]})
```

This creates a root user with the roles root - please select a secure password!

Now we need to stop our container. Issue
```
sudo docker ps
```
and grab the container id of the container with the "mongo" image.

Stop it using
```
sudo docker stop [container id]
```

and remove it (it'll be recreated) using
```
sudo docker container rm [container id]
```

Now lets create another mongo-container with authentication enabled:
```
sudo docker run -d -p 27017:27017 -v /home/twasi/beta/db:/data/db mongo mongod --auth
```
This instance will share the volume with the first one, and therefore it will have our root user created. Now we can connect to the database and create an user for twasi (we need to authenticate from here on, just use the password created before):

```
mongo -u root -p [passwordCreatedBefore] localhost/admin
```
We are now able to create an user with readWrite permissions on twasidb:
```javascript
db.createUser({user: "twasi", pwd: "anothers3cur3p4ssw0rd", roles:["readWrite"]})
```
exit with CTRL + C. Now the database is ready. Let's continue with starting twasi-core:
```
sudo docker run -p 8010:8000 -v /home/twasi/beta/twasi-core:/data twasi/twasi-core
```
We will:
- Map the host port 8010 to the container port 8000 (API).
- Map the host volume /home/twasi/beta/twasi-core to the container volume /data (You will install plugins there and manage your plugin.yml)

You should see the same input as when you start your .jar the first time. It will fail because there is no database connection - but a config file is created anyways. Stop the application using CTRL + C (it will time out after 30 seconds anyways). Now a config file should be created in the volume (under /home/twasi/beta/twasi-core/twasi.yml). Edit the database information. TODO: Config file documentation.

After setting up the config file, run twasi-core in deamon mode:
```
sudo docker run -d -p 8010:8000 -v /home/twasi/beta/twasi-core:/data twasi/twasi-core
```
