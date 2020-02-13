FROM jjanzic/docker-python3-opencv
# ENV LD_LIBRARY_PATH /usr/local/cuda/extras/CUPTI/lib64:$LD_LIBRARY_PATH
ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
RUN apt-get update --fix-missing && \
    apt-get install -y wget curl bzip2 ca-certificates libglib2.0-0 libxext6 libsm6 libxrender1 git mercurial subversion \
      autoconf automake libtool zlib1g-dev libicu-dev libpango1.0-dev libcairo2-dev \
      libgomp1 libgif7 libwebpmux3 libwebp6 libopenjp2-7 libpng16-16 libtiff5 zlib1g libopencv-dev libleptonica-dev swig \
      libxml2-dev fish fonts-ipafont fonts-ipaexfont fonts-noto-cjk libxml2 build-essential \
      android-tools-adb usbutils tesseract-ocr libtesseract-dev tesseract-ocr-jpn tesseract-ocr-eng  nodejs npm && \
    apt-get clean && rm -rf /var/lib/apt/lists/*
RUN TINI_VERSION=`curl https://github.com/krallin/tini/releases/latest | grep -o "/v.*\"" | sed 's:^..\(.*\).$:\1:'` && \
    curl -L "https://github.com/krallin/tini/releases/download/v${TINI_VERSION}/tini_${TINI_VERSION}.deb" > tini.deb && \
    dpkg -i tini.deb && \
    rm tini.deb && \
    rm -rf /var/lib/apt/lists/*
# "
RUN mkdir -p ~/.jupyter && { \
    echo "c.NotebookApp.allow_root = True"; \
    echo "c.NotebookApp.ip = '0.0.0.0'"; \
    echo "c.NotebookApp.token = ''"; \
    echo "c.JupyterLabTemplates.template_dirs = ['/home/template']"; \
    echo "c.JupyterLabTemplates.include_default = True"; \
    } | tee ~/.jupyter/jupyter_notebook_config.py
SHELL ["/bin/bash", "-c"]
    # pip install flake8 flake8-SQL flake8-bandit flake8-broken-line flake8-bugbear flake8-builtins flake8-import-order flake8-spellcheck flake8-strict flake8-string-format pandas-vet pep8-naming jupyter-lsp && \
RUN pip install jupyterlab psycopg2 matplotlib ipywidgets jupyter pandas pillow numpy scikit-image pyocr adbutils pure-python-adb pytesseract ipympl ipywidgets tqdm && \
    jupyter labextension install @jupyter-widgets/jupyterlab-manager && \
    jupyter labextension install jupyter-matplotlib
EXPOSE 8888
ENTRYPOINT [ "/usr/bin/tini", "--" ]
# CMD [ "/bin/bash" ]
