### Yii2VN - CMS base on Yii Framework version 2

#### Server information
* Nginx
* HHVM
* Redis
* MySQL

#### Example config virtual host in Nginx Server

```bash

server {
	set $ROOT /home/sieulog/Web
	listen 80;
	root $ROOT;
	index index.html index.htm index.php;
	server_name localhost;
	include hhvm.conf;
	location / {
		root $ROOT/frontend/web;
		try_files $uri /frontend/web/index.php?$args;
	}

	location ~* \.(htaccess|htpasswd|svn|git) {
		deny all;
	}

	location /admin {
		alias $ROOT/backend/web;
		try_files $uri /backend/web/index.php?$args;
	}
}

```