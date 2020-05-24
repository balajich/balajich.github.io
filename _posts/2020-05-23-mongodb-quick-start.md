---
title: "MongoDB Quick Start for development"
published: true
---

Start MongDB for development
- Clone repo https://github.com/balajich/mongodb.git
- Run mongodb in a docker container
- Use mongo client and mongo compass UI application to access database
- create a database called employeedb
- create a collection(tables) called employee
- insert data into table or documents
- find a record or a document
- stop the database
- delete the database

## Video
[![IMAGE ALT TEXT](http://img.youtube.com/vi/sNsWBswW2uk/0.jpg)](http://www.youtube.com/watch?v=sNsWBswW2uk "MongoDB Quick Start for development")

## Start mango db server in docker container
    docker-compose up -d
    
The above command will run the container in detached mode, or in the background for us. We are also mapping the container ports with host ports so that way we can access the database from a host level application if we wanted to.

## Use mongo client to connect to database server
    docker-compose exec mongodb mongo
    
The above command will connect to our deployment named mongodb using the interactive terminal and start the MongoDB shell client.

## List all existing database
    show dbs
    
## Create a database called employeedb
    use employeedb
    
No need to create a database before you run use command

## Create a collection(table) employee with data (documents)
    db.employee.save({id:1, firstname: "Leonardo", lastname: "DiCaprio" })
    db.employee.save({id:2,firstname: "Kate", lastname: "Winslet" })
    
Once collection is created database will be automatically created

## Query the collection(table)
    db.employee.find({ firstname: "Kate" })
Find employee with firstname as Kate

## Stop the database
    docker-compose stop

## Start the database
    docker-compose start

## Delete database and its data volume permanently
    docker-compose down -v


# References

- https://www.thepolyglotdeveloper.com/2019/01/getting-started-mongodb-docker-container-deployment/
- https://docs.mongodb.com/manual/tutorial/getting-started/
