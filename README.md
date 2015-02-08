guolin/shadowsocks-docker
====================

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
