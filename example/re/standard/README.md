# Easy Start

<p align="left">
    <b> English | <a href="https://github.com/zjunlp/DeepKE/blob/main/example/re/standard/README_CN.md">简体中文</a> </b>
</p>

## Requirements

> python == 3.8

- torch == 1.5
- hydra-core == 1.0.6
- tensorboard == 2.4.1
- matplotlib == 3.4.1
- scikit-learn == 0.24.1
- transformers == 3.4.0
- jieba == 0.42.1
- deepke 

## Download Code

```bash
git clone https://github.com/zjunlp/DeepKE.git
cd DeepKE/example/re/standard
```

## Install with Pip

- Create and enter the python virtual environment.
- Install dependencies: `pip install -r requirements.txt`.

## Train and Predict

- Dataset

  - Download the dataset to this directory.

    ```bash
    wget 120.27.214.45/Data/re/standard/data.tar.gz
    tar -xzvf data.tar.gz
    ```

  - The dataset is stored in `data/origin`:
    - `train.csv`: Training set
    -  `valid.csv `: Validation set
    - `test.csv`: Test set
    - `relation.csv`: Relation labels
  
- Training

  - Parameters for training are in the `conf` folder and users can modify them before training.
  - If using LM, modify 'lm_file' to use the local model.
  - Logs for training are in the `log` folder and the trained model is saved in the `checkpoints` folder.

  ```bash
  python run.py
  ```

- Prediction

  ```bash
  python predict.py
  ```

## Use models quickly


We align the relationship type and the entity type of [DUIE](https://ai.baidu.com/broad/download?dataset=dureader) with the cnschema

On this basis, two models are trained based on 'Chinese Bert WwM' and 'Chinese Roberta WwM ext'. The super parameters used in the model are the given parameters.

You can download the [model](https://drive.google.com/drive/folders/1wb_QIZduKDwrHeri0s5byibsSQrrJTEv) directly for experiments.You just need to modify the model path in `predict.yaml`,and then you can run you `predict.py` easily.


For example,input a sentence '东眼山森林游乐区位于桃园县与台北县交界的山林间，因山形酷似“向东眺望的大眼睛”而得名，海拔高度在650~1212公尺之间，面积916公顷，是台湾北部面积最大的森林游乐区' and entities '东眼山','1212公尺', DeepKE-chschema will output '海拔高度' aligning with cnschema.

## Models

1. CNN
2. RNN
3. Capsule
4. GCN
5. Transformer
6. Pre-trained Model (BERT)