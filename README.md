# DeadPoetSociety

This is an OIDC template for a course at EPITA.

# Requirement

## Docker compose

[Docker Compose](https://docs.docker.com/compose/) is required to run this example.

## Editing hosts

Add the following line to your hosts file to make domain names available on your computer

```
127.0.0.1	dps.epita.local
``` 

# Getting started

Run the following commands to run the example

```shell
# build images
docker compose build

# run containers
docker compose up
```

Following application are now available on your computer

| URL                            | Credentials                      | Description         |
|--------------------------------|----------------------------------|---------------------|
| https://dps.epita.local/       | N/A (publicly available)         | Apache public page  |
| https://dps.epita.local/auth   | user: admin<br>password: admin   | Keycloak admin page |
| https://dps.epita.local/python | user: python<br>password: python | Python webapp       |
| https://dps.epita.local/java   | user: user<br>password: user     | Java webapp         |

## Logout

You can logout to both application and identity provider by using front channel logout urls `https://dps.epita.local/redirect_oidc?logout=get`

See [module documentation](https://github.com/OpenIDC/mod_auth_openidc/wiki#9-how-do-i-logout-users) for more details
about logout.

# Usefull command
## Export keycloack config
In the container, run :
`/opt/keycloak/bin/kc.sh export --dir /opt/keycloak/data --realm easy-sso --users realm_file > conf.json`
