
# docker-mutli-php-versions

可直接运行的多版本PHP共存的Docker环境，目前支持 `php5.6` / `php7.2` / `php7.4` 共存。

# 文件结构

```
├── conf //配置文件
│   ├── nginx
│   │   ├── conf.d
│   │   │   ├── php56site.com.conf
│   │   │   ├── php72site.com.conf
│   │   │   └── php74site.com.conf
│   │   └── nginx.conf
│   └── php
│       ├── php-fpm.d
│       │   └── www.conf
│       └── php.ini
├── docker-compose.yml
├── log //日志文件
│   ├── nginx
│   │   ├── access.log
│   │   └── error.log
│   └── php-fpm
├── php
│   ├── php56
│   │   └── Dockerfile
│   ├── php72
│   │   └── Dockerfile
│   └── php74
│       └── Dockerfile
├── readme.md
└── site //网站目录
    ├── php56site
    │   └── index.php
    ├── php72site
    │   └── index.php
    └── php74site
        └── index.php
```

# 使用方法

启动：

```shell script

docker-compose up -d

```

停止：

```shell script

docker-compose stop

```

重启 nginx

```shell script

docker-compose restart nginx

```

进入 php 容器
```

docker-compose exec php56 /bin/bash

docker-compose exec php72 /bin/bash

docker-compose exec php74 /bin/bash
```
# 注意事项

1. 本地host配置
    - host文件需要添加指向本地配置的域名。
2. PHP插件安装
    - 在对应PHP版本的Dockerfile文件中使用`docker-php-ext-install`安装。
3. docker内网连接ip问题
    - 如果需要从内网中连接使用宿主机的ip，mac版本需要使用内置`docker.for.mac.host.internal`作为ip配置。
4. docker源速度问题
    - 可以添加国内源或者使用代理提速。
5. 容器内域名请求
    - 使用`network`中的别名`alias`实现容器内域名请求。
6. 镜像支持问题
    - 有些镜像比如php:7.4-fpm不再更新了，可以替换为php:7.4-fpm-bullseye之类的新版本，这个需要自行去docker hub找可以使用的镜像。 

# 参考

- [使用 Docker 秒速搭建多版本 PHP 开发环境](https://juejin.cn/post/6980576111818194957)
- [Docker构建包含PHP多版本的LNMP环境(php53,56,72)](https://0ne.store/2018/01/13/docker-compose-lnmp-multi-php-version/)
