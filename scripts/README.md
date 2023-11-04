#### Setup

```
docker stop keycloak_name && docker rm keycloak_name && \
docker stop postgres_name && docker rm postgres_name && \
docker volume rm postgres_data \
docker-compose up -d
```

##### Running on ports 8080

```
docker exec -it keycloak_prod sh
http://0.0.0.0:8080/auth/
http://localhost:8080/auth/
```

##### List databases (keycloak)

```
docker exec -it postgres_name psql -U postgres -c "\l"
```

##### Manually Setup Keycloak

```
Create Realm testrealms
Create Client testclient
Create user (user@email.com)
Create password (user@email.com)
Realm Settings -> Themes -> Login Theme -> testtheme

Keycloak Templates
Login Theme -> keycloak
Account Theme -> keycloak
Admin Theme -> keycloak
Email Theme ->
```

##### Copy Keycloak theme to Directory

**You can copy template.tfl and place it in theme folder**

Change favicon.ico

```
`-- themes
    `-- myTheme
       `-- login
           |-- resources
           |   |-- css
           |   |   |-- login.css
           |   |   `-- styles.css
           |   `-- img
           |       |-- favicon.ico
           |       |-- img-bg.png
           |       `-- img-text.png
           |-- template.ftl
           `-- theme.properties
```

```
sudo docker cp keycloak_prod:/opt/jboss/keycloak/themes/keycloak/ ./themes/new-theme

sudo docker cp keycloak_prod:/opt/jboss/keycloak/themes/keycloak ./themes/experiment-theme-1/experiment-theme
sudo docker cp keycloak_prod:/opt/jboss/keycloak/themes/base ./themes/experiment-theme-1/base

sudo docker cp keycloak_prod:/opt/jboss/keycloak/themes/keycloak ./themes/real-estate
sudo rm -r ./themes/real-estate
sudo chown work -R ./themes/real-estate
```

##### Setup for dev use

```
<script>
// refresh every 1 sec
    setInterval(() => {
      window.location.reload();
        console.log("refreshed")
    }, 1000);
</script>
```
