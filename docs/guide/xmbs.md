# 部署项目
本项目可以使用 `tomcat` 或者 `nginx` 部署，在这里分享下常规部署 `[Nginx]` 与使用Docker部署的两种方式
## SSH工具推荐
先分享个好用的 SSH 工具 [FinalShell](http://www.hostbuf.com/t/988.html)，后面部署会使用到 

#### 配置 nginx

我们可以使用 ```nginx``` 代理 ```java```服务，添加配置
```
server {
    listen 80;
    server_name 域名/当前服务器外网IP;
    location / {
        proxy_pass http://127.0.0.1:8000; #这里的端口记得改成项目对应的哦
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_set_header X-Forwarded-Port $server_port;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        }
    }
```
### 部署
