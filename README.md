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

# Proxy Pass

```
http {
		server {
		listen 80; # Assuming you want to serve on the default HTTP port

		server_name _;

		location / {
			proxy_pass http://localhost:3000; # Pass requests to your Rails app running on localhost
			proxy_set_header Host $host;
			proxy_set_header X-Real-IP $remote_addr;
			proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
			proxy_set_header X-Forwarded-Proto $scheme;
		}
	}

}

events {

}
```
