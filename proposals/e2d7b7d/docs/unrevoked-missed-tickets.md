(taken from a [gist](https://gist.github.com/davecgh/01fd24849a9e9a6d822d6d04eba7075d) by @davecgh, posted in #proposals on [2021-07-18](https://matrix.to/#/!qYpAAClAYrHaUIGkLs:decred.org/$-Z9EbAlzKZzGG0TQPnOcASk1zaAwFa3ciOUcFVeA2w4))

This script lists all unrevoked missed tickets and computes the total DCR locked in them.

```
#!/bin/sh

psql -U dcrdata -d dcrdata -A -t -c "SELECT best_block_height FROM meta;" > height.txt
psql -U dcrdata -d dcrdata -c "COPY (SELECT ticket_hash, height, trunc((price*1e8)::numeric) AS price FROM misses INNER JOIN tickets ON ticket_hash = tx_hash WHERE spend_tx_db_id IS NULL ORDER BY height, ticket_hash) TO STDOUT WITH CSV HEADER DELIMITER ',';" > unrevoked_misses.csv
echo "$(psql -U dcrdata -d dcrdata -A -t -c "SELECT trunc(SUM(price)::numeric, 8) FROM misses INNER JOIN tickets ON ticket_hash = tx_hash WHERE spend_tx_db_id IS NULL;") DCR" > sum.txt
```

As of block 572,954 (2021-07-19) the script lists 1,867 tickets and a total locked 196749.63979854 DCR.
