#### 1. 问题举例

单机同时安装两个nginx会提示已存在，使用Docker可以轻松构建多个docker镜像。

#### 2. 运行Docker镜像

启动第一个nginx镜像

```bash
docker run -d nginx:1.10.0
```

检查是否启动

```bash
docker ps
```

启动第二个nginx镜像

```bash
docker run -d nginx:1.9.3
```

#### 4. Docker容器交互命令

查看具体容器信息（xxxx代表container id或container names）

```bash
docker inspect xxxx
```

停止容器

```bash
docker stop container_id
```

删除容器

```bash
docker rm container_id
```

#### 5. 创建镜像

下载代码库

```bash
git clone https://github.com/udacity/ud615.git
```

构建静态二进制文件

```bash
cd ud615/app/monolith
go get -u
go build --tags netgo --ldflags '-extldflags "-lm -lstdc++ -static"'
```

构建应用容器

```bash
docker build -t monolith:1.0.0 .
```

添加标签

```
docker tag monolith:1.0.0 <your username>/monolith:1.0.0
```

登录DockerHub并发布应用

```bash
docker login
docker push <your username>/monolith:1.0.0
```

