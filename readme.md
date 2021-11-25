
# docker-mutli-php-versions

多版本PHP共存的Docker环境，目前支持php5.6以及php7.2共存

# 文件结构

```
├── conf //配置文件
│   ├── nginx
│   │   ├── conf.d
│   │   │   ├── php56site.com.conf
│   │   │   └── php72site.com.conf
│   │   └── nginx.conf
│   └── php
│       ├── php-fpm.d
│       │   └── www.conf
│       └── php.ini
├── docker-compose.yml
├── log //日志文件
│   ├── nginx
│   │   ├── access.log
│   │   └── error.log
│   └── php-fpm
├── php
│   ├── php56
│   │   └── Dockerfile
│   └── php72
│       └── Dockerfile
├── readme.md
└── site //网站文件
    ├── php56site
    │   └── index.php
    └── php72site
        └── index.php
```

# 使用方法

# 注意事项