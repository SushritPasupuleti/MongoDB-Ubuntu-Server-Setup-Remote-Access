# MongoDB-Ubuntu-Server-Setup-Remote-Access

 Setup MongoDB on ubuntu-server along with remote access configs

## Install Mongo on Ubuntu

[Follow the official guide](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/)

## Setup Admin

```mongo
use admin;

db.createUser({
      user: "admin",
      pwd: "myadminpassword",
      roles: [
                { role: "userAdminAnyDatabase", db: "admin" },
                { role: "readWriteAnyDatabase", db: "admin" },
                { role: "dbAdminAnyDatabase",   db: "admin" }
             ]
  });
```

## Setup DB Users with Roles

```mongo
db.createUser({
      user: "user1",
      pwd: "user1password",
      roles: [
                { role: "userAdmin", db: "sampledb" },
                { role: "dbAdmin",   db: "sampledb" },
                { role: "readWrite", db: "sampledb" }
             ]
  });
```

## Enable MongoDB Auth

```bash
sudo nano /etc/mongod.conf
```

Add the following line

```yaml
security:
    authorization: 'enabled'
```