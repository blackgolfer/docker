# docker
## Jupyterlab
```shell
cd jupyterlab
docker build --tag="jupyterlab-anaconda3:latest" -f Dockerfile .
docker image prune
docker run -v $PWD/app:/app -it -p 8888:8888 blackgolfer/jupyterlab-anaconda3
```