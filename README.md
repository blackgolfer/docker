# docker
## 系统设置与管理
[docker-systemd]: https://docs.docker.com/config/daemon/systemd/ "Control Docker with systemd"
[archlinux-docker-wiki]: https://wiki.archlinux.org/index.php/Docker "Docker"
[archlinux-docker-tutorial-1]: https://linuxhint.com/arch-linux-docker-tutorial/ "Arch Linux Docker Tutorial"
[systemd-docker-container-1]: https://blog.container-solutions.com/running-docker-containers-with-systemd "Running Docker Containers with Systemd"
[docker-secret-1]: https://blog.mikesir87.io/2017/05/using-docker-secrets-during-development/ "Using Docker Secrets during Development"
[docker-restart-1]: https://docs.docker.com/config/containers/start-containers-automatically/ "Start containers automatically"
[docker-secret-2]: https://howchoo.com/g/zwzkzduwmjy/getting-started-with-docker-secrets "Getting Started with Docker Secrets"
[docker-registry]: https://hub.docker.com/_/registry "registry --- docker official image"

- [Control Docker with systemd][docker-systemd]
- [Arch Linux Docker Wiki][archlinux-docker-wiki]
- [Arch Linux Docker Tutorial][archlinux-docker-tutorial-1]

### 迁移docker数据文档

如果docker服务器正在运行中，首先将服务器停下来：

```shell
# systemctl stop docker.service
```

然后按以上资料里所描述的方法去设置`data-root`。docker默认的数据文档是`/var/lib/docker`, 以下指令将原来的数据（images, containers等等）迁移到新的目录：

```shell
# mkdir /new/path/docker
# rsync -aqxP /var/lib/docker/ /new/path/docker
```

设置`data-root`的三种方法：
1. `/etc/docker/daemon.json`：需要手动创建。
      ```json
      {
            "data-root": "new/path/docker"
            "storage-drive": "overlay2"
      }
      ```
2. `/etc/systemd/system/docker.service.d/docker-storage.conf `：需要手动创建文档目录`/etc/systemd/system/docker.service.d`和文件`docker-storage.conf`
      >[Service]\
ExecStart= \
ExecStart=/usr/bin/dockerd --data-root=/new/path/docker -H fd://

3. `docker.service`：在archlinux这个文件在`/etc/systemd/system/multi-user.target.wants/`里面，不建议这样做。
      >FROM:\
ExecStart=/usr/bin/docker daemon -H fd://\
TO:\
ExecStart=/usr/bin/docker daemon -g /new/path/docker -H fd://

### 自动启动docker container
#### restart
- [Start containers automatically][docker-restart-1]

#### 用systemd来启动
- [Running Docker Containers with Systemd][systemd-docker-container-1]

### docker secret
- [Using Docker Secrets during Development][docker-secret-1]
- [Getting Started with Docker Secrets][docker-secret-2]

## 私有仓库
《循序渐渐学Docker》第7.2节。
### 安装docker-registry
- [registry --- docker official image][docker-registry]

Docker官方提供了`docker-registry`的镜像，
```shell
# docker run --name docker-registry --restart always -d -p 5000:5000 registry
```

## 项目管理
[docker-project-example-1]: https://github.com/archlinux/archlinux-docker "Docker Base Image for Arch Linux"
[bash-script-tutorial-1]: https://linuxconfig.org/bash-scripting-tutorial-for-beginners "Bash Scripting Tutorial for Beginners"
[bash-script-tutorial-2]: https://www.lifewire.com/pass-arguments-to-bash-script-2200571 "How to Pass Arguments to a Bash Script"


   1. 各项目中的Makefile文件参考《[Docker Base Image for Arch Linux][docker-project-example-1]》
   2. bash脚本参考资料：
      - [Bash Scripting Tutorial for Beginners][bash-script-tutorial-1]
      - [How to Pass Arguments to a Bash Script][bash-script-tutorial-2]

产生docker镜像：
```shell
make docker-image
```

发布docker镜像：
```shell
make docker-push
```

## 数据共享
[data-sharing-1]: https://www.digitalocean.com/community/tutorials/how-to-share-data-between-docker-containers "How To Share Data between Docker Containers"
[data-sharing-2]: https://www.digitalocean.com/community/tutorials/how-to-share-data-between-the-docker-container-and-the-host "How To Share Data Between the Docker Container and the Host"

## compose设置共享
[docker-compose-sharing-1]: https://docs.docker.com/compose/extends/ "Share Compose configurations between files and projects"
[docker-compose-sharing-2]: https://stackoverflow.com/questions/45915182/docker-compose-sharing-container-between-multiple-projects-by-using-the-same-co "docker-compose: Sharing container between multiple projects by using the same container_name"
[docker-compose-sharing-3]: https://www.chrisblunt.com/rails-on-docker-share-containers-across-multiple-projects/ "Rails on Docker: How to Share Containers Across Multiple Projects"
[docker-compose-sharing-4]: https://docker-curriculum.com/#multi-container-environments "Multi-container Environments"

*参考资料*：
- [Share Compose configurations between files and projects][docker-compose-sharing-1]
- [docker-compose: Sharing container between multiple projects by using the same container_name][docker-compose-sharing-2]
- [Rails on Docker: How to Share Containers Across Multiple Projects][docker-compose-sharing-3]
- [Multi-container Environments][docker-compose-sharing-4]

### 多个compose文件
### 服务扩展
### 设置的增加与覆盖

## Kubernetes
[kubernetes-archlinux-doc]: https://wiki.archlinux.org/index.php/Kubernetes "Archlinux wiwi: Kubernetes"
[kubernetes-containers-1]: https://kubernetes.io/docs/tasks/access-application-cluster/communicate-containers-same-pod-shared-volume/ "Communicate Between Containers in the Same Pod Using a Shared Volume"

*参考资料*：
- [Archlinux wiki: Kubernetes][kubernetes-archlinux-doc]
- [Communicate Between Containers in the Same Pod Using a Shared Volume][kubernetes-containers-1]
