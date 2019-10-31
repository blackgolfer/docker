FROM continuumio/miniconda3

RUN mkdir /app

WORKDIR /app

ADD . /app

RUN apt-get -y update && apt-get -y install build-essential git-core

RUN conda config --add channels conda-forge
RUN conda install -y --file requirements.conda.txt
RUN pip install -r requirements.pip.txt

RUN mv /app/.jupyter /root/.jupyter
RUN mv /app/theme /opt/conda/share/jupyter/lab/themes/@jupyterlab/theme-light-extension

RUN python -m spacy download en_core_web_lg

# So that custom modules can be loaded from anywhere.
ENV PYTHONPATH="/app:${PYTHONPATH}"
# Point to configuration folder on host.
ENV IPYTHONDIR="/app/.ipython"
# We want unbuffered Python
ENV PYTHONUNBUFFERED=TRUE

EXPOSE 8888:8888
ENTRYPOINT [ "jupyterlab", "lab", "--allow-root", "--ip=0.0.0.0", "--no-browser", "--port=8888", "--notebook-dir=/app"]
