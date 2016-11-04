#Terminal Cheat Sheet

## Disk space
Show size of folders in a given folder

```
du -sh ~/*/
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

## Imagick

Create a animated gif with an interval of 30 ms while resizing it to 20%

```
convert -resize 20% -delay 30 -loop 0 funny_*.jpg funny.gif
```

Replace the eight frame with the same frame but another duration
```
convert funny_orignal.gif \( -clone 8 -set delay 120 \) -swap 8 +delete funny_new.gif
```
