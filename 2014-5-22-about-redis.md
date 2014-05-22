##about redis

1. 安装
`$ wget http://download.redis.io/releases/redis-2.6.17.tar.gz`

`$ tar zxvf redis-2.6.17.tar.gz`		

`$ cd redis-2.6.17.tar.gz`

`make `

2. make出现问题解决：
- 删除解压文件夹，重新解压，
- 然后在 `redis-2.6.17/src/Makefile`开头添加 `CFLAGS= -march=i686`
- `make`

3. 运行redis `src/redis-server`

4. 在另外一个终端打开redis-cli `src/redis-cli`

5. 测试
```
[root@localhost redis-2.6.17]# src/redis-cli
redis 127.0.0.1:6379> set foo bar
OK
redis 127.0.0.1:6379> get foo
"bar"
```

## 使用redis
1. 一些基本的命令
- flushdb 清空内存
- keys * 查看所有
```
redis 127.0.0.1:6379> keys *
1) "foo"
```

2. string类型
- set key value 	设置key对应的值为string类型的value,返回1表示成功，0失败
- setnx key value 	同上，如果key已经存在，返回0 。nx 是not exist的意思
- get key 			获取key对应的string值,如果key不存在返回nil
- getset key value 	设置key的值，并返回key的旧值。如果key不存在返回nil

```
redis 127.0.0.1:6379> set foo bar
OK
redis 127.0.0.1:6379> setnx foo bar
(integer) 0
redis 127.0.0.1:6379> getset foo andy
"bar"
redis 127.0.0.1:6379> get foo
"andy"
```

--------