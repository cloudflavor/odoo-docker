Odoo docker image
---
This repo is a replica of the [original odoo docker repo](https://github.com/odoo/docker) but it has the env variables modified so
that the app can run on top of kubernetes.

`docker pull cloudflavor/odoo-docker:latest`

Changes:

Commented out
```
#: ${HOST:=${DB_PORT_5432_TCP_ADDR:='db'}}
#: ${PORT:=${DB_PORT_5432_TCP_PORT:=5432}}
#: ${USER:=${DB_ENV_POSTGRES_USER:=${POSTGRES_USER:='odoo'}}}
#: ${PASSWORD:=${DB_ENV_POSTGRES_PASSWORD:=${POSTGRES_PASSWORD:='odoo'}}}

```

And pointed Env vars to ones generated.
```
check_config "db_host" "$ODOO_DB_SERVICE_HOST"
check_config "db_port" "$ODOO_DB_SERVICE_PORT"
check_config "db_user" "$USER"
check_config "db_password" "$PASSWORD"
```
