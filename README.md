Concise docker image with RDKit source build
------

## A motivation
What do you feel when you use RDKit with python in docker?
I always feel confused in situations in which it is impossible to achieve both the customizability of environments and the smallness of docker containers.
I want to use python of the specific version in small docker container (not in Anaconda), therefore, this source was developed.

## Basic environments
+ OS: ubuntu16.04 (as the upstream image)
+ Python: 3.5.5
+ RDKit: Release_2017_09_3

## Usages
This image is supposed to be used as a base image for your docker container. But if you use this image, you type a following command
```bash
$ docker run -i -t nyuge/rdkit-build
```

It is good for you to use this image as an upstream image, as follows:
```
FROM nyuge/rdkit-build

RUN pip install --no-cache-dir --upgrade \
    chainer \
    scikit-learn \
    tqdm
RUN pip install --no-cache-dir --upgrade \
    chainer-chemistry \
    && mkdir -p $HOME/workspace
WORKDIR $HOME/workspace/
```

## Reference
+ [RDKit repository](https://github.com/rdkit/rdkit): The cheminformatics and machine-learning soft ware
+ [Chainer Chemistry: A Library for Deep Learning in Biology and Chemistry](https://github.com/pfnet-research/chainer-chemistry)
+ [Dockerfile for building RDKit](https://github.com/InformaticsMatters/rdkit/tree/Release_2017_03_1): The docker image with python2.7 and source-built RDKit
+ [alpine-rdkit](https://github.com/kubor/alpine-rdkit): The docker image with Miniconda3 and binary-installed RDKit
