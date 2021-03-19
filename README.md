## Concept Learners for Few-Shot Learning
Kaidi Cao*, Maria Brbić*, Jure Leskovec

[Project website](http://snap.stanford.edu/comet)
_________________

### Dependencies

The code is built with following libraries:


- [PyTorch](https://pytorch.org/) 1.5
- [anndata](https://icb-anndata.readthedocs-hosted.com/en/stable/anndata.AnnData.html)
- [scanpy](https://icb-scanpy.readthedocs-hosted.com/en/stable/)
- json
- [wandb](https://www.wandb.com/)

```
pip install scanpy --ignore-installed llvmlite
pip install wandb
pip install anndata
```

### Getting started

##### CUB dataset
* Change directory to `comet/CUB/filelists/CUB/`
* Run `source ./download_CUB.sh`

##### Tabula Muris dataset
* Change directory to `comet/TM/filelists/tabula_muris/`
* Run `source ./download_TM.sh`

### Usage

##### Training

We provide an example here:

Run
```cd comet/CUB/```

```python ./train.py --dataset CUB --model Conv4NP --method comet --train_aug```

##### Testing

We provide an example here:

Run
```python ./test.py --dataset CUB --model Conv4NP --method comet --train_aug```

### Tabula Muris benchmark

If you would like to test your algorithm on the new benchmark dataset introduced in our work, you can download the data as described above or directly at [http://snap.stanford.edu/comet/data/tabula-muris-comet.zip](http://snap.stanford.edu/comet/data/tabula-muris-comet).

Dataset needs to be preprocessed using [preprocess.py](https://github.com/snap-stanford/comet/blob/master/TM/data/preprocess.py). Train/test/validation splits are available in [load_tabula_muris](https://github.com/snap-stanford/comet/blob/master/TM/data/dataset.py). 

Running this code requires [anndata](https://icb-anndata.readthedocs-hosted.com/en/stable/anndata.AnnData.html) and [scanpy](https://icb-scanpy.readthedocs-hosted.com/en/stable/) libraries.
