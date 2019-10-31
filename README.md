# docker
--------

[docker-project-example-1]: https://github.com/archlinux/archlinux-docker "Docker Base Image for Arch Linux"

## 项目管理
   1. 各项目中的Makefile文件参考《[Docker Base Image for Arch Linux][docker-project-example-1]》

产生docker镜像：
```shell
make docker-image
```

发布docker镜像：
```shell
make docker-push
```
