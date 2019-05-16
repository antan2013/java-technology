## Nginx

### 1  Linux的安装

* 一键安装依赖

  ```shell
  
  yum -y install gcc zlib zlib-devel pcre-devel openssl openssl-deve
  ```

  

  配置文件

  ```java
  server {
          listen       80;
          server_name  自己的域名;
  
          proxy_set_header X-Forwarded-Host $host;
          proxy_set_header X-Forwarded-Server $host;
          proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  
          location / {
  			proxy_pass http://127.0.0.1:9001 要转发的位置;
  			proxy_connect_timeout 600;
  			proxy_read_timeout 600;
          }
      }
  	server {
          listen       80;
          server_name  自己的域名;
  
          proxy_set_header X-Forwarded-Host $host;
          proxy_set_header X-Forwarded-Server $host;
          proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  
          location / {
  			proxy_pass http://127.0.0.1:10010 要转发的位置;
  			proxy_connect_timeout 600;
  			proxy_read_timeout 600;
          }
      }
  ```

  指令：

  - 启动：`start nginx`
  - 停止：`nginx-s stop`
  - 重新加载：`nginx -s reload`

  

####详情查看FastDFS的安装