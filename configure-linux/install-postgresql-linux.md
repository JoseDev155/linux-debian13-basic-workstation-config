# Install PostgreSQL in Linux

## Install PostgreSQL in Debian 13

### Install PostgreSQL 17

Go to the site [PostgreSQL Download for Debian](https://www.postgresql.org/download/linux/debian/).

Go to **Automated repository configuration** section and execute (as root or with `sudo`):

```bash
apt install -y postgresql-common
/usr/share/postgresql-cpmmon/pgdg/apt.postgresql.org.sh
```

If we have `systemd`, it create a symlink automatically.

For we have access to all complete versions, we have to configure the repository with the commands in
**To manually configure the Apt repository, follow these steps** section (as root or with `sudo`):

```bash
# Import the repository signing key:
apt install curl ca-certificates
install -d /usr/share/postgresql-common/pgdg
curl -o /usr/share/postgresql-common/pgdg/apt.postgresql.org.asc --fail https://www.postgresql.org/media/keys/ACCC4CF8.asc

# Create the repository configuration file:
. /etc/os-release
sh -c "echo 'deb [signed-by=/usr/share/postgresql-common/pgdg/apt.postgresql.org.asc] https://apt.postgresql.org/pub/repos/apt $VERSION_CODENAME-pgdg main' > /etc/apt/sources.list.d/pgdg.list"

# Update the package lists:
apt update

# Install the latest version of PostgreSQL:
# If you want a specific version, use 'postgresql-17' or similar instead of 'postgresql'
apt -y install postgresql
```

If we execute:

```bash
apt update -y
```

We have an error "It cannot read `pgdg.sources`", because it has the old format.

The, go to:

```bash
cd /etc/apt/sources.list.d/
```

Is we have Debian 13 Trixie **testing** or **unestable**, we delete `pgdg.list`.

If we have Debian 13 Trixie **stable** delete the file (as root or with `sudo`):

```bash
rm -r pgdg.sources
```

And now, we execute (as root or with `sudo`):

```bash
apt update && apt upgrade -y
```

To install PostgreSQL 17 (as root or with `sudo`):

```bash
apt -y install postgresql-17
```

First, we did `apt -y install postgresql`, but that installed the basic version or common. And that command
this is for the PostgreSQL 17 complete.

We have options in the **Packages** section.

### To get up the service

Previously, this created us a symblink for `postgresql-common`, but no for `postgresql-17`. 

So, we move to:

```bash
cd /var/lib/postgresql/
```

And list all versions:

```bash
ls
```

We sjee a dir with the name `17/`. If we move to the version and execute `ls`, we can see a file called `main`.
This tells us that we installed it correctly.

Now, we execute:

```bash
systemctl start postgresql.service
```

We check the status:

```bash
systemctl status postgresql.service
```

This must say `active`.

For enable in the boot:

```bash
systemctl enable postgresql.service
```

### Basic comands in PosgreSQL

Login in PostgreSQL:

```bash
su - postgres
```

Start PostgreSQL:

```bash
psql
```

For help:

```bash
help
```

For list all roles:

```bash
\du
```

Create DB:

```bash
create database winda;
```

Select DB:

```bash
select datname from pg_database;
```

**Exercise**

Create user:

```bash
create user alan with password 'Anime#123';
```

Execute:

```bash
\du
```

Login with user `alan`:

```bash
psql -U alan -h localhost -d postgres;
```

To see the config file:

```bash
show config_file;
```

To see the data dir:

```bash
show data_directory;
```

For exit to PostgreSQL:

```bash
\q
```

Logout from PostgreSQL:

```bash
exit
```

To stop the service:

```bash
systemctl stop postgresql
```

Check the status:

```bash
systemctl status postgresql
```

This must say `inactive`.

To make modifications, we must be `inactive` the service. Then, we can start the service:

```bash
systemctl start postgresql
```

Check the status:

```bash
systemctl status postgresql
```

This must say `active`.

## References

* Link to the YouTube video: [Postgresql 17 in Debian 13 Trixie](https://youtu.be/ZV-MlFuFnVU?si=s7DnVd4324IVvDUY)
