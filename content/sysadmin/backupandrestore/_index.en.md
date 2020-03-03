---
title: "Backup and restore"
menu:
  main:
    name: "Backup and restore"
    identifier: "sysadmin/backupandrestore"
    parent: "sysadmin"
    weight: -944
---

# Backup and restore

## Securing the assets

Backup the directory that you specified for the data store during the [installation](../installation).

This means you have saved everything, including your assets.

But the information about the assets needs special care - they are stored in PostgreSQL databases, which could also change during backup.

## Backup the databases

The easydb internally uses two PostgreSQL databases. To copy them consistently, you have two options:

_Either - very simple:_

__A.__ Stop the easydb while backing up the data store.

_Or - our recommendation:_

__B.__ Use the PostgreSQL-specific tool `pg_dump`.

Pg_dump saves in a format which is still compatible after software updates.

The space requirement is also lower than with method A - if you exclude `pgsql/var` while saving the data storage.

## Backup using pg_dump

```bash
DATABASE=easydb5

docker exec easydb-pgsql pg_dump -U postgres -v -Fc -f /backup/$DATABASE.pgdump $DATABASE

docker exec easydb-pgsql pg_dump -U postgres -v -Fc -f /backup/eas.pgdump eas
```

Remarks:

- The easydb can and should run during this backup method. At least the component "easydb-pgsql" has to run.
- You will then find the backup files in the subdirectory `pgsql/backup/` of the data store defined during the [installation](../installation).
- If you first run pg_dump and then backup the data store, then you also include the dump files automatically.

To display the database names you use, use the following:

```bash
docker exec easydb-pgsql psql -U postgres -l
```

They are typically eas and easydb5 (or eas and easydb).

&nbsp;

## maintenance contract

If you have a maintenance contract with us, we will let the linux host make dumps of the databases each night.

You can choose how many of them will be kept and at which time they are made. By default 7 dumps (one week) will be kept and the dump will be made each night at a time specified in a cron job file inside the directory `/etc/cron.d/`.

The dumps will be placed in the subdirectory `pgsql/backup/` of the data store defined during the [installation](../installation) (default: `/srv/easydb/`).

&nbsp;

# Restore a backup copy

1. Stop the easydb. (Described at the [top](#Operation) of this page)
2. Replace the contents of the data store with the backup copy. You have defined the data store at the [installation](../installation).
3. Start the first part of easydb - the component "easydb-pgsql". This is the first start command in the section "[Start](../installation)" of the installation.
4. If available, use the backup created by pg_dump:

```bash
DATABASE=easydb5
docker exec -i -t easydb-pgsql psql -U postgres -c 'DROP   DATABASE "eas"'
docker exec -i -t easydb-pgsql psql -U postgres -c 'DROP   DATABASE "'$DATABASE'"'
docker exec -i -t easydb-pgsql psql -U postgres -c 'CREATE DATABASE "eas"'
docker exec -i -t easydb-pgsql psql -U postgres -c 'CREATE DATABASE "'$DATABASE'"'
docker exec -i -t easydb-pgsql pg_restore -U postgres -v -d eas    /backup/eas.pgdump
docker exec -i -t easydb-pgsql pg_restore -U postgres -v -d $DATABASE /backup/$DATABASE.pgdump
```

5. Now start the remaining components. To do this, use the remaining start commands in the [Start](../installation) section.