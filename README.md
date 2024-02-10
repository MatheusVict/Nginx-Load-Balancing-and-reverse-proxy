# Nginx Studies

* First add bash and vim on nginx container

```shell
docker compose exec nginx apk add bash vim
```

* After that execute bash

```shell
docker compose exec nginx bash
```
* And change defalult.conf to use reverse proxy and load balancing

```shell
vim /etc/nginx/conf.d/default.conf 
```

and add this to have a load balancing with reverse proxy:

```file
upstream name_of_your_balance {
    server your_server_url;
    server your_server_url;
    server your_server_url;
    server your_server_url;
}

server {
    listen 80;
    server_name localhost;

    location /(tis is the relative pah) {
        proxy_pass name_of_your_balance
    }
}
```

