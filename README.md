# docker_lnmp

- nginx/1.12.1
- mysql/5.6.16
- php/7.1.18
- redis/2.8.19
- mongodb/3.2.13

## 使用

``` bash
# 安装
git clone https://github.com/chenenkou/docker_lnmp.git

# 复制.env.example为.env，按需修改.env
WWW_PATH=~

# 启动
docker-compose up -d
```

## 参考

- [Docker — 从入门到实践](https://docker_practice.gitee.io/)
- [Docker在PHP项目开发环境中的应用](https://avnpc.com/pages/build-php-develop-env-by-docker)
- [OMGZui/lnmp](https://github.com/OMGZui/lnmp)