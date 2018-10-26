# nginx重定向

### http重定向到https
```
server {  
    listen  111.11.1.111:80;  
    server_name test.com;  
      
    rewrite ^(.*)$  https://$host$1 permanent;  
} 
```