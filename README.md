# pkredis_4x_cok

## Intro
### Install
```
apt install build-essential && mkdir /redis && cd /redis
wget http://download.redis.io/releases/redis-4.0.8.tar.gz
tar zxvf redis-4.0.8.tar.gz
cd redis-4.0.8
```
make a configure folder
```
mkdir /redis/conf
cp redis.conf /redis/conf
cd deps
make hiredis lua jemalloc linenoise
make
make PREFIX=/redis install
```

apt:
```
apt-get update && apt install redis-server
```


### Getting ready
```
bin/redis-server conf/redis.conf
```
To run redis in background
```
daemonize yes
```
use init.d to start redis
```
/etc/init.d/redis-server start
```
kill redis
```
kill ` pidof redis-server`
```
Or
``` 
bin/redis-cli shutdown   = SIGTERM 15
```



### Connecting to Redis with redis-cli
```
bin/redis-cli
```


### Getting server information
```
info
```


### Understanding the Redis protocol
RESP
- REdis Serialization Protocol

test
```
echo -e "*1\r\n$4\nPING\r\n" | nc 127.0.0.1 6379
```

### String
To overwrite part of the string.
```
SETRANGE "key" 10 "newstr"
```

data types:```OBJECT ENDOCING mykey```
- int
- embstr (less or equal 44 bytes)
- raw

##### LINSERT
```
LNISERT key after "VALUE2" "VALUE5"
```








## Developing with Redis







## Setting Up High Availablity and Cluster
### When to use Redis
### Session store
Redis is a perfect session store because it has very low access latency compared to a RDBMS. 
Also, key expiration support in Redis can be
naturally adopted for session timeout management.
```



### Latest N records
Ten resturants that have been most recently added to our application.
RDBMS
```
select * from restaurants order by created_at desc limit 10;
```
redis
```
lpush restaurant
ltrim restaurant 0 10
```


### Using the correct data types
