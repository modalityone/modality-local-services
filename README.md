# Modality Local Services

This repository contains a Docker-based solution for running Postgres locally, as required by Modality. Install once, then start and stop as necessary during development. Additional notes are provided for connecting a Postgres client directly to the database.



## INSTALLATION
### 1. Install Docker
Please install [Docker Desktop](https://www.docker.com/products/docker-desktop) on your local machine if you do not have it already. If using a Mac, the easiest way is to install using `brew`. Please provide Docker with a minimum of 8GB of RAM, ideally more.


### 2. Clone the repository
```shell
mkdir -vp modality-local-services
export MODALITY_LOCAL_SERVICES=${PWD}/modality-local-services
cd $MODALITY_LOCAL_SERVICES
git clone https://github.com/modalityone/modality-local-services.git .
```


### 3. Import SQL Setup Scripts
Locate the SQL setup scripts in the main Modality repository:

[SQL setup scripts](https://github.com/modalityone/modality/tree/main/modality-base/modality-base-server-datasource/src/main/resources/db-pristine)

And copy the scripts into the Postgres data directory:

`$MODALITY_LOCAL_SERVICES/data/postgres/`


### 4. Setup Environment Variables
Environment variables store the Postgres database name, username and password. Defaults are provided in the `.env-template`. Use this template file as the basis for your Docker-based configuration, by creating an `.env` file from it. You may leave the defaults, or provide new values accordingly:

```shell
cp .env-template .env
source .env # make the environment variables available to the shell
```


### 5. Build Postgres Container
```shell
docker-compose build --no-cache
```


## DAILY USE
### Start Postgres Container
```shell
docker-compose up
```


### Stop Postgres Container
```shell
docker-compose down
```



## DATABASE CLIENT CONNECTION
Postgres clients can connect to the running Postgres container using the following credentials (contained within the `.env` file):

* Server: 127.0.0.1
* Port: 5432
* Database: modality
* User: modality
* Password: modality
