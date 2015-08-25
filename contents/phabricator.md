# Phabricator

## Apache reverse proxy

```
<VirtualHost *:80>
    ServerName phab.rosonix.twbbs.org
    ServerAdmin webmaster@phab.rosonix.twbbs.org

    CustomLog ${APACHE_LOG_DIR}/phab-access.log combined
    ErrorLog ${APACHE_LOG_DIR}/phab-error.log
   
    ProxyPass / http://127.0.0.1:8081/
    ProxyPassReverse / http://127.0.0.1:8081/
    ProxyPreserveHost On
</VirtualHost>
```

## Apache server

```
<VirtualHost *:80>
    # Change this to the domain which points to your host.
    ServerName phab.rosonix.twbbs.org

    ServerAdmin webmaster@phab.rosonix.twbbs.org

    # Change this to the path where you put 'phabricator' when you checked it
    # out from GitHub when following the Installation Guide.
    #
    # Make sure you include "/webroot" at the end!
    DocumentRoot /home/phabricator/phabricator/webroot

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    RewriteEngine on
    RewriteRule ^/rsrc/(.*)     -                       [L,QSA]
    RewriteRule ^/favicon.ico   -                       [L,QSA]
    RewriteRule ^(.*)$          /index.php?__path__=$1  [B,L,QSA]
    <Directory "/home/phabricator/phabricator/webroot">
        Require all granted
    </Directory>
</VirtualHost>
```

## Run on docker

Deprecated:

```sh
docker run --name phab -p 8081:80 -p 22:22 -p 22280:22280 --link phab-mysql:database -d changyuheng/phabricator bash -c "source /etc/apache2/envvars; /usr/sbin/apache2 -DFOREGROUND"
```

Updated:

```sh
docker run --name phab -p 8081:80 -p 22:22 -p 22280:22280 --link phab-mysql:database -it changyuheng/phabricator bash
```

More updated:

```sh
docker run -d --name phab -p 8081:80 -p 22:22 -p 22280:22280 --link phab-mysql:database --entrypoint=/entrypoint.sh changyuheng/phabricator
```

## Start the daemons

At `phabricator/ $`

```sh
source /etc/apache2/envvars; /usr/sbin/apache2
sudo -u phabricator /home/phabricator/phabricator/bin/phd restart
sudo -u phabricator /home/phabricator/phabricator/bin/aphlict restart
/usr/sbin/sshd -f /etc/ssh/sshd_config.phabricator
```