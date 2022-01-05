# Setup Web Server use Bitnami Images and custom it

Create Docker web server

- PHP-FPM
- MariaDB or MySQL
- Nginx

Instruction:

- Copy environment variables sample `.env.exampl` to `.env`
- Change the environment variables for your application requirement

## PHP-FPM

You can custom PHP version, read Bitnami PHP-FPM

- [PHP-FPM doc](https://bitnami.com/stack/phpfpm/containers)

## NGINX

You can custom NGINX version, read Bitnami NGINX

- [Nginx doc](https://bitnami.com/stack/nginx/containers)

## Database

You can custom MySQL version, read Bitnami MARIADB or MySQL:

- [MariaDB doc](https://bitnami.com/stack/mariadb)
- [MySQL doc](https://bitnami.com/stack/mysql)

## WEB APPLICATION

> Place your application in `public-html` directory

## NGINX VIRTUAL HOST

> Place your custom virtual file `(\*.conf)` host in `/config/nginx/vhosts` directory

Sample file server block config `mytest.com.conf`:

```bash
server {
  listen 0.0.0.0:8080;
  server_name mytest.com;

  root /app/test;

  location / {
    try_files $uri $uri/index.php;
  }

  location ~ \.php$ {
    # fastcgi_pass [PHP_FPM_LINK_NAME]:9000;
    fastcgi_pass phpfpm:9000;
    fastcgi_index index.php;
    include fastcgi.conf;
  }
}
```

## REGISTER DOMAIN NAME TO THE HOST

> Windows 8/10 OS : edit file C:\Windows\System32\Drives\etc\host

> Linux/Unix OS : edit file /etc/hosts

## License

MIT / BSD

## Author Information

[JogjaScript](https://jogjascript.com)

This :pencil: was created in 2021 by :smile: [Asapdotid](https://github.com/asapdotid).
