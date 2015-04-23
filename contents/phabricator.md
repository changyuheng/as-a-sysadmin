# Phabricator

## Run on docker

```sh
docker run --name phab -p 8081:80 -p 22:22 -p 22280:22280 --link phab-mysql:database -d changyuheng/phabricator bash -c "source /etc/apache2/envvars; /usr/sbin/apache2 -DFOREGROUND"
```