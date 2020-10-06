FROM jupyter/scipy-notebook 
# jupyter/tensorflow-notebook

USER root

WORKDIR /home/analyst

COPY requirements.txt .
RUN pip install -r requirements.txt --trusted-host pypi.python.org --trusted-host files.pythonhosted.org --trusted-host pypi.org && \
    rm -f requirements.txt

RUN jupyter labextension install @jupyterlab/toc --no-build && \
    # jupyter labextension install dask-labextension --no-build &&\
    # jupyter serverextension enable dask_labextension && \
    jupyter serverextension enable --py jupyterlab_git && \
    jupyter lab build && \
    jupyter lab clean && \
    jlpm cache clean && \
    npm cache clean --force && \
    rm -rf $HOME/.node-gyp && \
    rm -rf $HOME/.local

EXPOSE 5000
EXPOSE 8050

ENTRYPOINT ["jupyter", "lab", "--ip=0.0.0.0", "--allow-root"]
