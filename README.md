# PostgreSQL Setup on a Linux Machine

## Step 1: Update Package Lists and Install PostgreSQL

```bash
sudo apt update
sudo apt install postgresql postgresql-contrib
```

## step 2 : switching to the PostgreSQL User

```bash
sudo -i -u postgres
```

## step 3 : Access the PostgreSQL Promt

```bash
psql
```

## step 4 : Create New Superuser

```sql
CREATE USER admin_user WITH SUPERUSER PASSWORD 'your_password';
```

## step 5: create a New Database Owned by the New User

```sql
CREATE DATABASE my_database OWNER admin_user;
```

## step 6: Edit the PostgreSQL Authentication Configuration

```bash
sudo nano /etc/postgresql/15/main/pg_hba.conf
```

## Step 7: Modify Authentication Methods in pg_hba.conf

```text
# "local" is for Unix domain socket connections only
local   all             all                                     md5

# IPv4 local connections:
host    all             all             127.0.0.1/32            md5

# IPv6 local connections:
host    all             all             ::1/128                 md5
```

## Step 8: Restart the PostgreSQL Service

```bash
sudo systemctl restart postgresql
```

## Step 9: Test the Admin User Login

```bash
psql -U admin -d postgres -W
```

## Step 10: Create an 'admin' Database

```bash
sudo -i -u postgres
psql
CREATE DATABASE admin;
\q
psql -U admin -d admin -W
```
