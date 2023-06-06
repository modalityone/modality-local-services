# Modality Local Services

This repository contains a Docker-based solution for running Postgres locally on the developers machine. Install once, then start and stop as necessary during development. Additional notes are provided before for connecting a Postgres client directly to the database.


## Installation
### 1. Install Docker
Please install link:https://www.docker.com/products/docker-desktop/[Docker Desktop^] on your local machine if you do not have it already. If using a Mac, the easiest way is to install using `brew`. Please provide Docker with a minimum of 8GB of RAM, ideally more.


### 2. Import SQL Setup Scripts
Get the SQL setup scripts from the Modality repository at the following location:

`$MODALITY_ROOT/modality-base/modality-base-server-datasource/src/main/resources/db-pristine/*.sql`

Copy the scripts into the following directory:

`$MODALITY_LOCAL_SERVICES/data/postgres/`


### 3. Setup Environment Variables
Environment variables store the Postgres database name, username and password. Defaults are provided in the `.env-template`. Use this template file as the basis for your Docker-based configuration, by creating an `.env` file from it. You may leave the defaults, or provide new values accordingly:

```shell
cp .env-template .env
source .env # make the environment variables available to the shell
```


### 4. Build Postgres Container
```shell
docker-compose build --no-cache
```


## Daily Use
### Start Postgres Container
```shell
docker-compose up
```


### Stop Postgres Container
```shell
docker-compose down
```


## Database Client Connection
Postgres clients can connect to the running Postgres container using the following credentials (contained within the `.env` file):

* Server: 127.0.0.1
* Port: 5432
* Database: modality
* User: modality
* Password: modality



project documentation, which you can view on the website [here][modality-docs].

[modality-docs]: https://docs.modality.one
