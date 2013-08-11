# Dockerfile PostgreSQL

## Info

This Dockerfile creates a container running PostgreSQL 9.2.4.

Here's what it does in particular:

- building Postgresql using [dockyard](https://github.com/dynport/dockyard)
- exposing it on port `5432`
- initializes a database in `/var/lib/postgresql/9.2/main`
- inserts a superuser in the database: `docker:d0cker` (change in the Dockerfile)


## Install

- `docker build -t "postgresql:9.2.4" .`
- `docker run -d postgresql:9.2.4`


## Persistance

You can mount the database directory as a volume to persist your data:

`docker run -d -v $HOME/.d_volumes/postgres/:/var/lib/postgresql postgresql:9.2.4`

But before you can do so you first need to create the source folder: `mkdir -p $HOME/.d_volumes/postgres`


## TODO

- Clean Shutdown of the `postgresql` process on SIGTERM (maybe using `trap` in the start script)


## Meta

Build with docker version `0.5.1`
