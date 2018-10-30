# `docker` support for LibreHealth

To start a simple `lh-ehr` instance, follow the steps:

## Getting started

### 1. Get the source code (if not already)

    $ git clone https://github.com/LibreHealthIO/lh-ehr.git

### 2. Build the `librehealth` docker image

Build using your desired `php` version, by picking from the following: `php7.0-apache`, **`php7.1-apache`** (default), `php7.2-apache` (more: [hub.docker:_/php](https://hub.docker.com/_/php/)). Currently only *-apache* (a.k.a [Apache HTTP Server](https://httpd.apache.org/)) is supported.

    $ cp .env.mysql.example .env.mysql ; cp .env.ehr.example .env.ehr
    $ docker-compose -p librehealth up -d

Go to [http://localhost:8000/setup.php](http://localhost:8000/setup.php). At this point the default image will guide you throught the installation steps.

### 4. Installation

**Optional Site ID Selection**

Site ID: `default`

-> Continue

**LibreHealth EHR Setup**

-> Continue

**LibreHealth EHR Setup - Step 1**

Choose: _I have already created the database_

-> Continue

**LibreHealth EHR Setup - Step 2**

MYSQL SERVER:
Server Host: `db`
Server Port: `3306`
Database Name: `libreehr`
Login Name:	`libreehr`
Password: `s3cret`

LibreHealth EHR USER:
Initial User: `<your admin user>`
Initial User Password: `<your admin password>`
Initial User's First Name: `<John>`
Initial User's Last Name: `<Doe>`
Initial Group: `Default`

**LibreHealth EHR Setup - Step 3**

-> Continue

**LibreHealth EHR Setup - Step 4**

-> Continue

**LibreHealth EHR Setup - Step 5**

-> Continue

**LibreHealth EHR Setup - Step 6**

-> Continue

**LibreHealth EHR Setup**

Follow link [Click here to start using LibreHealth EHR](http://localhost:8000/?site=default).

### 5. Use

Login with credentials provided above:
* Initial User: `<your admin user>`
* Initial User Password: `<your admin password>`

## Cleanup

    $ docker-compose down -p librehealth -v

## Backup (make use of volumes)

The volumes that needs to be backed up: `librehealth_db_data` and `librehealth_sites`

    $ docker volume ls | grep librehealth
    local               librehealth_db_data
    local               librehealth_sites
