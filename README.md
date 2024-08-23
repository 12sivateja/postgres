# postgres

## Setup of the postgres in the linux machine

step -1
sudo apt update
sudo apt install postgresql postgresql-contrib

step - 2
sudo -i -u postgres

step - 3
psql

step -4
CREATE USER admin_user WITH SUPERUSER PASSWORD 'your_password';

step -5
CREATE DATABASE my_database OWNER admin_user;

step - 6
sudo nano /etc/postgresql/15/main/pg_hba.conf

step -7
`
# "local" is for Unix domain socket connections only

local all all md5

# IPv4 local connections:

host all all 127.0.0.1/32 md5

# IPv6 local connections:

host all all ::1/128 md5
`

step -8
sudo systemctl restart postgresql

step - 9
psql -U admin -d postgres -W `for the tesing of the admin login`

step - 10
sudo -i -u postgres
psql
create database admin

\q

psql -u admin -d admin - W
