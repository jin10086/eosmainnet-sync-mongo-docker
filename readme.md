# EOSMAINNET-SYNC-MONGO-DOCKER

## 使用的镜像

- [mongo](https://hub.docker.com/_/mongo/)

如果mongo要使用密码的话，可以参考上面的链接.并修改 `eosdata/config.ini`里面的`mongodb-uri`就可以了.

- [eos](https://github.com/EOS-Mainnet/eos/tree/master/Docker)

## 如何使用

### 第一次的话
`docker-compose -f docker-compose-init.yml up -d`

### 除了第一次以外

`docker-compose up -d`

如果中断了，则直接使用 `docker-compose start`

想暂停的话 `docker-compose stop`

### 报错 `generic server error`

再试一次同样的命令就可以了

### 报错 `database dirty flag set (likely due to unclean shutdown): replay required`

执行 `docker-compose -f docker-compose-replay.yml up -d`就可以了

一般出现这种情况都是docker意外关闭导致的，所以关闭docker最好使用 `docker-compose stop`

### 如果想重新同步的话，就按照第一次的操作

## mongo 使用

默认是在主机 27018端口,有需要的话，可以自行修改.

## 查看log

查看nodeos log
`docker logs -f eosmainnet-sync-mongo-docker_nodeosd_1`

查看 mongo log
`docker logs -f eosmainnet-sync-mongo-docker_nodeosd_1`

