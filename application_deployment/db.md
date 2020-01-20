## Deploy database on Openshift

### Deploy application

To create a database which you can then connect to, run the command:
```
oc new-app postgresql-ephemeral --name database --param DATABASE_SERVICE_NAME=database --param POSTGRESQL_DATABASE=sampledb --param POSTGRESQL_USER=username --param POSTGRESQL_PASSWORD=password
```
This will start up an instance of a PostgreSQL database.

When using a database with your front end web application, you will need to configure the web application to know about the database. We are going to skip that in this course.

### Check rollout 


To monitor progress as the database is deployed and made ready, run the command:
```
oc rollout status dc/database
```


This command will exit once the database is ready to be used.


In order to know where the database is running to connect to, run the command:
```

oc get pods --selector app=database
```
This will output the details of the pod which is running the database.
```
NAME               READY     STATUS    RESTARTS   AGE
database-1-9xv8n   1/1       Running   0          1m
```

To make it easier to reference the name of the pod, capture the name of the pod in an environment variable by running:

POD=`oc get pods --selector app=database -o custom-columns=name:.metadata.name --no-headers`; echo $POD

To create an interactive shell within the same container running the database, you can use the oc rsh command, supplying it the name of the pod.

oc rsh $POD
You could also access an interactive terminal session via a web browser by visiting the pod details from the web console.

You can see that you are in the container running the database by running:

ps x

This will display output similar to:

PID TTY      STAT   TIME COMMAND
  1 ?        Ss     0:00 postgres
 60 ?        Ss     0:00 postgres: logger process
 ...
 
 
 Because you are in the same container, you could at this point run the database client for the database if provided in the container. For PostgreSQL, you would use the psql command.

psql sampledb username

This will present you with the prompt for running database operations via psql.

psql (9.5.4)
Type "help" for help.

sampledb=>
You could now dynamically create database tables, add data, or modify existing data.

To exit psql enter:

\q

To exit the interactive shell run:

exit

Anything you want to do to the database could be be done through any database admin tool included in the container.



If you need to run database script files to perform operations on the database, you would also need to first copy those files into the database container using the oc rsync command.
