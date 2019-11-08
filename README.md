# docker
--------

[docker-project-example-1]: https://github.com/archlinux/archlinux-docker "Docker Base Image for Arch Linux"
[bash-script-tutorial-1]: https://linuxconfig.org/bash-scripting-tutorial-for-beginners "Bash Scripting Tutorial for Beginners"
[bash-script-tutorial-2]: https://www.lifewire.com/pass-arguments-to-bash-script-2200571 "How to Pass Arguments to a Bash Script"

## 项目管理
   1. 各项目中的Makefile文件参考《[Docker Base Image for Arch Linux][docker-project-example-1]》
   2. bash脚本参考资料：[Bash Scripting Tutorial for Beginners][bash-script-tutorial-1], [How to Pass Arguments to a Bash Script][bash-script-tutorial-2]

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


*参考资料*：
- [Share Compose configurations between files and projects][docker-compose-sharing-1]
- [docker-compose: Sharing container between multiple projects by using the same container_name][docker-compose-sharing-2]
- [Rails on Docker: How to Share Containers Across Multiple Projects][docker-compose-sharing-3]

### 多个compose文件
### 服务扩展
### 设置的增加与覆盖

## Kubernetes
[kubernetes-containers-1]: https://kubernetes.io/docs/tasks/access-application-cluster/communicate-containers-same-pod-shared-volume/ "Communicate Between Containers in the Same Pod Using a Shared Volume"

*参考资料*：
- [Communicate Between Containers in the Same Pod Using a Shared Volume][kubernetes-containers-1]