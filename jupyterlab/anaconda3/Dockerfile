FROM continuumio/anaconda3

RUN mkdir /app

WORKDIR /app

ADD . /app

# So that custom modules can be loaded from anywhere.
ENV PYTHONPATH="/app:${PYTHONPATH}"
# Point to configuration folder on host.
ENV IPYTHONDIR="/app/.ipython"
# We want unbuffered Python
ENV PYTHONUNBUFFERED=TRUE

COPY bin/entrypoint.sh /usr/local/bin/
COPY config/ /root/.jupyter/

EXPOSE 8888:8888
#CMD jupyter lab --port=8888 --ip=0.0.0.0 --allow-root --notebook-dir=/app --no-browser
ENTRYPOINT ["entrypoint.sh"]