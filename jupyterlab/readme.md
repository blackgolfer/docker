# Jupyterlab Using Docker
-------------------------
## 参考文献
[docker-compose-python-jupyter-1]: https://dev.to/rosejcday/using-docker-compose-for-python-and-jupyter-4nbd "Using docker-compose for Python and Jupyter"
[MongoConda]: https://github.com/juandados/MongoConda "A docker-compose project including Python 3, Jupyter, Mongo databases and Web Service with Flask"
[docker-jupyterlab-1]: https://github.com/amalic/Jupyterlab "Jupterlab Docker container"
[docker-jupyterlab-2]: https://github.com/caseware/jupyterlab-docker "CaseWare JupyterLab"

   1. [Using docker-compose for Python and Jupyter][docker-compose-python-jupyter-1]
   2. [A docker-compose project including Python 3, Jupyter, Mongo databases and Web Service with Flask][MongoConda]
   3. [Jupterlab Docker container][docker-jupyterlab-1]
   4. [CaseWare JupyterLab][docker-jupyterlab-2]

## 项目
### Jupyterlab容器
这个项目主要参考《[Jupterlab Docker container][docker-jupyterlab-1]》
#### continuumio/anaconda3
##### 抓取镜像
   <div class="highlight sh">
     <pre>
       <span class="gp">&dollar;</span> docker pull blackgolfer/jupyterlab-anaconda3
     </pre>
   </div>

##### 运行
进入jupyterlab项目的根目录，这里我们假设这个根目录下的app/文件夹作为jupyterlab的工作区，
   <div class="highlight sh">
     <pre>
       <span class="gp">&dollar;</span> docker run --rm -v $PWD/app:/app -it -p 8888:8888 blackgolfer/jupyterlab-anaconda3
     </pre>
   </div>


#### continuumio/miniconda3
[CaseWare JupyterLab][docker-jupyterlab-2]