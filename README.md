guolin/shadowsocks-docker
====================

[中文简介](#中文简介)

docker image to run a shadowsocks server

Setting a specific configration
-------------------------------------------------

If you want to use a preset configration instead of a default, you can set 
the environment variable, eg

* server address: $SS_SERVER_ADDR  default 0.0.0.0
* server port: $SS_SERVER_PORT default 8388
* password: $SS_PASSWORD default password
* encryption method: $SS_METHOD default aes-256-cfb [others](https://github.com/shadowsocks/shadowsocks/wiki/Encryption)
* timeout: $SS_TIMEOUT default 300


Usage
-----

To create the image `guolin/shadowsocks`, execute the following command on the guolin/shadowsocks folder:

        docker build -t guolin/shadowsocks .


Running the shadowsocks server
--------------------------

Run the following command to start shadowsocks:

        docker run -d -p 8838:8838 guolin/shadowsocks

The first time that you run your container, a default password(password) will be set. You can get the password, check the logs of the container by running:

        docker logs <CONTAINER_ID>

You will see an output like the following:

        ========================================================================
        You can now connect to this ShadowSocks server:"

        server: 0.0.0.0  port: 8838 password: password

        Please remember the password!!
        ========================================================================

Done!


中文简介
=========
shadowsocks 主要是用于翻墙。
我的实际使用方法是直接在tutum上创建一个digitalocean的docker主机，然后运行这个image，通过ENV的方式进行基本的配置，然后就可以轻松翻墙了。

具体的配置如下：
---------

通过环境变量的方式实现

* server address: $SS_SERVER_ADDR  默认 0.0.0.0
* server port: $SS_SERVER_PORT 默认 8388
* password: $SS_PASSWORD 默认 password
* encryption method: $SS_METHOD 默认 aes-256-cfb [others](https://github.com/shadowsocks/shadowsocks/wiki/Encryption)
* timeout: $SS_TIMEOUT 默认 300

一般情况只需要改密码就可以了。

TUTUM 使用方法
----------
1. 设置环境变量的密码。
2. 设置对外端口。

通过日志可以查看具体的配置情况。

Docker 使用方法
------

docker run -d -p 8838:8838 -e SS_PASSWORD=[替换成自己的密码] guolin/shadowsocks

