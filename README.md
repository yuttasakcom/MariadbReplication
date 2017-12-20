# Mariadb Replication

## Master
mysql -u root -p

create user 'repl'@'%' identified by 'slavepassword';

grant replication slave on *.* to 'repl'@'%';

create database pets;

create table pets.cats (name varchar(20));

insert into pets.cats values ('fluffy');

select * from pets.cats;


## Slave
db02 -> mysql -u root -p
CHANGE MASTER TO
-> MASTER_HOST='db01',
-> MASTER_USER='repl',
-> MASTER_PASSWORD='slavepassword';

start slave;
show slave status\G;

show slave hosts;