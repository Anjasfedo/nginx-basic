NGINX is open-source web server software used for reverse proxy, load balancing, and caching. It's important to understand, especially for backend developer.

server: nginx, serve web content to browser (web server)

client - network - nginx - server

can be incraise server, and serve to network as one server? (nginx)

reverse proxy, load balancer, encryption, scalability

# Serve Static Conten

```
http {
	server {
		listen 8080;
		root /var/www/nginx-basic;
		index index.html;
	}
}
events {

}
```

- Make sure to give proper access to the file

# Mime Types

```
http {

	include mime.types;

	server {
		listen 8080;
		root /var/www/nginx-basic/;
		index index.html;

		location / {
			try_files $uri $uri/ =404;
		}

		location /css/ {
			try_files $uri $uri/ =404;
		}
	}
}

events {

}
```
