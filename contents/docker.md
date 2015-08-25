# Docker

## Backup

### MySQL

```sh
cd ~/<empty_folder>
docker run --volumes-from phab-mysql -v $(pwd):/backup busybox tar cvf /backup/phab-mysql-volume.tar /var/lib/mysql
docker export phab-mysql > phab-mysql.tar
```

### Phabricator

```sh
cd ~/<empty_folder>
docker export phab > phab.tar
```