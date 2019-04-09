Deploy Postgres in OS, the in the psql in the Postgres Pod:

$ createuser --interactive --pwprompt
Enter name of role to add: mydb
Enter password for new role: mydb
Enter it again: mydb
Shall the new role be a superuser? (y/n) y

$ createdb -O mydb mydb
$ psql --user=mydb
mydb=# GRANT all ON database mydb TO mydb;
mydb=# create table foo (id as varchar(255));
mydb=# select * from foo;
 id
----
(0 rows)

In the application deployment config:

ENV_FILES=/opt/eap/standalone/configuration/*.env

The app will be available locally as:

https://eap-pg-4-myproject.127.0.0.1.nip.io/eap-postgres-db/
