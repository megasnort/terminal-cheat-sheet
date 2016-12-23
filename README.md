#Terminal Cheat Sheet

## Disk space
Show size of folders, in a given folder and sort descending by size (in MB)

```
sudo du -sBM /home/* | sort -nr
```

Show free space on all drives

```
df -h
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

## Archives

Zip a folder, and exclude certain files

```
zip -r file.zip folder -x *.git* *.DS_Store *.sass-cache*
```

