## Concept Learners for Few-Shot Learning
Kaidi Cao*, Maria Brbić*, Jure Leskovec

[Project website](http://snap.stanford.edu/comet)
_________________

### Main code

[write_CUB_filelist.py](https://github.com/e96031413/comet/blob/master/CUB/filelists/CUB/write_CUB_filelist.py):從這個檔案可以理解dataset被寫入到json檔案時，包含了label_names, image_names, image_labels, part(每個concept的bounding box位置)

[train.py](https://github.com/e96031413/comet/blob/master/CUB/train.py)：主訓練程式，首先載入base.json和val.json(line 68~69)，由[write_CUB_filelist.py](https://github.com/e96031413/comet/blob/master/CUB/filelists/CUB/write_CUB_filelist.py)產生，並透過SetDataManager的get_data_loader載入(line 124)、載入comet(line 134)

[comet.py](https://github.com/e96031413/comet/blob/master/CUB/methods/comet.py)：comet方法的程式碼位置

[datamgr.py](https://github.com/e96031413/comet/blob/master/CUB/data/datamgr.py)：載入dataset及data transform的方法(get_data_loader in line 76)

[dataset.py](https://github.com/e96031413/comet/blob/master/CUB/data/dataset.py)：完整處理資料集的程式。self.meta(line 69)載入base.json和val.json，self.sub_meta(line 79)加入concept的bounding box位置、SubPartsDataset的sub_meta應該是把指定範圍的圖片都載入、self.num_joints有15代表CUB預設所提供的15個concept(line 182)，其中，joints_vis應該是把bounding box加入到圖片裡面(line 166)、data_numpy代表圖片的位置路徑轉成numpy的變數。

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
pip install goatools
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
