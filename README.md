# Nginx Image with static file caching
Uses [flashspys/nginx-static](https://github.com/flashspys/docker-nginx-static) as the base.

Full nginx config:
```nginx
server {
    listen       80;
    server_name  localhost;

    location / {
        root   /static;
        index  index.html index.htm;
    }

    location ~* \.(?:ico|css|js|gif|jpe?g|png)$ {
        expires 180d;
        add_header Pragma public;
        add_header Cache-Control "public";
    }
}
```