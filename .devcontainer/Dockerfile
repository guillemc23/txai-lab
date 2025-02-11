FROM jupyter/datascience-notebook:python-3.11

USER root

RUN apt-get update

RUN apt-get update \
    && echo "Updated apt-get" \
    && apt-get install -y openjdk-8-jre \
    && echo "Installed openjdk 8"

USER ${NB_UID}

RUN pip install pyppeteer
RUN pyppeteer-install

RUN conda install -y -q -c conda-forge pydot python-graphviz
RUN conda install -y -q -c conda-forge py4j

RUN pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118

# I1 dependencies
RUN curl https://github.com/cmencar/py4jfml/raw/refs/heads/master/dist/py4jfml-1.0.tar.gz \
    && pip install py4jfml-1.0.tar.gz \
    && rm -rf py4jfml-1.0.tar.gz

# I2 dependencies
RUN pip install simplenlg tabulate interpret xgboost dice_ml opencv-python --quiet

WORKDIR "${HOME}"
