# Terminal Cheat Sheet

## Disk space
Show size of folders, in a given folder and sort descending by size (in MB)

```
sudo du -sBM /home/* | sort -nr
```

Show free space on all drives

```
df -h
```

## UFW

Show rules

```
ufw status numbered
```

Delete rule

```
ufw remove 1
```

Add rule

```
ufw allow 8000
```

## PyPi
Create distribution

```
python setup.py sdist bdist_wheel --universal
```

Upload to PyPi

```
twine upload dist/*
```

## Find

Find a file in a given dir with a given name

```
find ~ -type f -name test.txt
```


Find files that were modified a day ago

```
find ~ -type f -mtime -1
```

## Webcam in OSX is not working

```
sudo killall VDCAssistant
```

## Recursive chmodding

Recursively chmod only directories

```
find . -type d -exec chmod 755 {} \;
```

Recursively chmod only files
```
find . -type f -exec chmod 644 {} \;
```

Recursively set the execute bit on every directory

```
chmod -R a+X *
```

Recursively chmod only PHP files (with extension .php)

```
find . -type f -name '*.php' -exec chmod 644 {} \;
```

## Imagick

Create a animated gif with an interval of 30 ms while resizing it to 20%

```
convert -resize 20% -delay 30 -loop 0 funny_*.jpg funny.gif
```

Replace the eight frame with the same frame but another duration
```
convert funny_orignal.gif \( -clone 8 -set delay 120 \) -swap 8 +delete funny_new.gif
```

## Images

Make a smaller png

```
pngcrush image.png -rem alla -reduce -brute result.png
```


## File transfer

Copy one file on a remote (listed in ~/.ssh/config as `my_server`) to local home directory. 

```
scp my_server:/path/of/file.zip ~
```

Copy the contents of one folder to another (verbose, archive, zip)

```
rsync -vaz {location} {host}:{destination}
```

## Sass
Start SASS watcher that generates a compressed .css-file

```
sass --watch --style compressed style.scss:style.css
```

## Postgres

Create a utf 8 database databasename with owner username:
```
createdb -Ousername -Eutf8 databasename
```

Make a dump of a database

```
pg_dump -f ~/database.sql -Ocx databasename
```

Create/delete databases and users

```
createdb databasename
createuser username
dropdb databasename
dropuser username
```

Start postgres on osx

```
pg_ctl -D /usr/local/var/postgres -l /usr/local/var/postgres/server.log start
```

## Docker
Remove all docker crap

```
docker rm $(docker ps -a -q)
docker rmi $(docker images -q)
docker network rm $(docker network ls -q)
docker run --rm -v /var/lib/docker/network/files:/network busybox rm /network/local-kv.db
```

Start a docker machine
```
docker-machine create --driver virtualbox --virtualbox-disk-size "40000" default
docker-machine start default
eval $(docker-machine env lets)
```

Remove a docker machine
```
docker-machine stop default
docker-machine rm default
```

Go into a docker container

```
docker exec -it name_of_docker_container bash
```

## Archives

Zip a folder, and exclude certain files

```
zip -r file.zip folder -x *.git* *.DS_Store *.sass-cache*
```

## Git

Change the last commit, message and conten

```
git commit --amend -m "Also check for empty files" --no-edit
```

Add a tag

```
git tag -a v0.0.1 -m "The very first version, supporting FileFields"
```

## Letsencrypt

### old way
Modify the domains of a certificate

```
/opt/letsencrypt/letsencrypt-auto --expand -d www.domain.com -d domain.com -d other.area.com
```

Renew the certificates

```
/opt/letsencrypt/letsencrypt-auto renew >> /var/log/letsencrypt
```

### new way
Add a domain/certificate

```
sudo certbot certonly --authenticator standalone --pre-hook "service apache2 stop" --post-hook "service apache2 start"
```

Refresh the certificates

```
sudo certbot certyonly renew
```

## ln

Create symbolic link

```
ln -s /target/to/which/the/link/should/go target-name 
```

## User management

Add user

```
sudo adduser user_name
```

Add existing user to group

```
usermod -a -G group_name user_name
```

invalidate password of user

```
sudo chage -d 0 camiel
```

Which groups does a user belong to?

```
groups user_name
```

## PHP
Restart php service on ubuntu

```
sudo service php5-fpm reload
```

Restart php service in OSX (brew)

```
brew services restart php70
```


## tar

Untar and -zip a file.

```
tar -zxvf {file.tar.gz}
```
