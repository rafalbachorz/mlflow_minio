FROM ubuntu:18.04
MAINTAINER rafal@bachorz.eu

RUN apt-get update && apt-get install -y curl libpq-dev build-essential

# Install miniconda to /miniconda
RUN curl -LO http://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
RUN bash Miniconda3-latest-Linux-x86_64.sh -p /miniconda -b
RUN rm Miniconda3-latest-Linux-x86_64.sh
ENV PATH=/miniconda/bin:${PATH}
RUN conda update -y conda

RUN conda install -y pip

COPY requirements.txt /tmp
WORKDIR /tmp

EXPOSE 5000
RUN pip install -r requirements.txt

RUN mkdir /mlruns
WORKDIR /mlruns

#CMD mlflow server \
#        --host 0.0.0.0 \
#        --backend-store-uri sqlite:///mlruns.db \
#        --default-artifact-root ${ARTIFACT_ROOT}
#CMD ["mlflow", "server", "-h", "0.0.0.0", "--backend-store-uri", "sqlite:///mlruns.db", "--default-artifact-root", ${ARTIFACT_ROOT}]
#CMD ["mlflow", "server", "-h", "0.0.0.0", "--backend-store-uri", "file:///tmp/mlruns", "--default-artifact-root", "artifacts"]
