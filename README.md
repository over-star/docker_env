DNMP（Docker + Nginx + MySQL + PHP7 + Redis）
qq
qqqq
ssss## 1.快速使用
1. 拷贝并命名配置文件（Windows系统请用`copy`命令），启动：
    ```

    $ cd docker_env                                       # 进入项目目录
    $ docker-compose up -d                                # 启动
    ```


### 2.Nginx使用
```bash
$ docker exec -it nginx nginx -s reload
```
这里两个`nginx`，第一个是容器名，第二个是容器中的`nginx`程序。


### 3.安装PHP扩展
打开你的`.env`文件修改如下的PHP配置，增加需要的PHP扩展：
```bash
PHP_EXTENSIONS=pdo_mysql,opcache,redis       # PHP 要安装的扩展列表，英文逗号隔开
```

然后重新build PHP镜像。
```bash
docker-compose stop php
docker-compose build php
```


## 4.管理命令
### 4.1 服务器启动和构建命令
如需管理服务，请在命令后面加上服务器名称，例如：
```bash
$ docker-compose up -d                      # 创建并且后台运行方式启动所有容器
$ docker-compose up -d nginx php  mysql     # 后台运行的方式启动nginx、php、mysql容器
$ docker-compose start php                  # 启动服务
$ docker-compose stop php                   # 停止服务
$ docker-compose restart php                # 重启服务
$ docker-compose build php                  # 构建或者重新构建服务
$ docker-compose rm php                     # 删除并且停止php容器
$ docker-compose down                       # 停止并删除容器，网络，图像和挂载卷
```

### 4.2 添加快捷命令

打开`~/.bashrc`或者`~/.zshrc`文件，加上：
```bash
alias dnginx='docker exec -it nginx /bin/sh'
alias dphp='docker exec -it php /bin/sh'
alias dmysql='docker exec -it mysql /bin/bash'
alias dredis='docker exec -it redis /bin/sh'
```
下次进入容器就非常快捷了，如进入php容器：
```bash
$ dphp
```

## License
MIT


