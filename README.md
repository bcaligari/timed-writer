# timed-writer

`write()` a block to a file every so many seconds with or without an exclusive lock.

```{text}
Usage: ./timed-writer [-s SLEEP ] [-c MAX_ITER] [-f MAX_FAIL] [-b BLOCK_SIZE] [-l] FILENAME
       ./timed-writer -h

Writes a line to FILENAME with SLEEP seconds between writes

        -s SLEEP      : seconds sleep after each iteration (default: 5; bounds: [1, 3600])
        -c MAX_ITER   : limit iterations to MAX_ITER (def: 666)
        -f MAX_FAIL   : limit consecutive write() failures to MAX_FAIL <= 100 (def: 5; inf: 0)
        -b BLOCK_SIZE : set write() size to BLOCK_SIZE <= 33554432 (def: 0)
                        0 writes iteration's "%d\n"
        -l            : place LOCK_EX on FILENAME

Example: ./timed-writer /mnt/myfile.txt
         ./timed-writer -s 5 -c 100 -l /mnt/myexlusive.txt
         ./timed-writer -s 1 -c 10 -f 2 -b $((1024*1024)) -l /mnt/megwrite.txt
```
