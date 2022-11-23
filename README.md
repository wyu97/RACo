## Code for Retrieval Augmentation for Commonsense Reasoning

### Introduction of RACo

- This is the official resources of our **EMNLP 2022** paper **"Retrieval Augmentation for Commonsense Reasoning: A Unified Approach"** [\[arXiv\]](https://arxiv.org/abs/2210.12887).

### Step0 Download the Commonsense Corpus

- Corpus (20M): Google drive [\[link\]](https://drive.google.com/drive/folders/1oj2POBBy8kyBFNU5nHb05wu2DlcOfGnV?usp=share_link) 

- Code: Official DPR code [\[link\]](https://github.com/facebookresearch/DPR) 
    
    - first run `python merge-corpus.py` to construct corpus
    - modify the [retrieval corpus path](https://github.com/facebookresearch/DPR/blob/a31212dc0a54dfa85d8bfa01e1669f149ac832b7/conf/ctx_sources/default_sources.yaml#L5) in above the DPR code

### Step1 Training: Commonsense Retriever

- Training Data: Google drive [\[link\]](https://drive.google.com/drive/folders/1abY1yMj9ygF7Plb52sDEBsKqn4GlwlBx?usp=share_link) 

- Code: Official DPR code, same as above. 

    - modify the [training data path](https://github.com/facebookresearch/DPR/blob/a31212dc0a54dfa85d8bfa01e1669f149ac832b7/conf/datasets/encoder_train_default.yaml#L45) as 

    ```
    raco_train:
        _target_: dpr.data.biencoder_data.JsonQADataset
        file: {your folder path}/train.json
    
    raco_dev:
        _target_: dpr.data.biencoder_data.JsonQADataset
        file: {your folder path}/dev.json
    ```

### Step1 Inference: Retrieve Documents 

- Inference Data: Google drive [\[link\]](https://drive.google.com/drive/folders/1VMpi4hl1VYuaBPhC3gB4PDTVlXdl-6Sn?usp=share_link)

- Code: Official DPR code, same as above. 

    - modify the [inference data path](https://github.com/facebookresearch/DPR/blob/a31212dc0a54dfa85d8bfa01e1669f149ac832b7/conf/datasets/retriever_default.yaml#L35) as 

    ```
    {dataset}_train:
        _target_: dpr.data.retriever_data.CsvQASrc
        file: {your folder path}/{dataset}/train.tsv
    
    {dataset}_dev:
        _target_: dpr.data.retriever_data.CsvQASrc
        file: {your folder path}/{dataset}/dev.tsv

    {dataset}_test:
        _target_: dpr.data.retriever_data.CsvQASrc
        file: {your folder path}/{dataset}/test.tsv
    ```

### Step2 Training and Inference: Commonsense Reader 

- Training Data: obtained from the last step

- Code: Official FiD code [\[link\]](https://github.com/facebookresearch/FiD) 


### Step2: FiD Outputs Evaluation 

- Accuracy is the same as exact match in FiD code.

- BLUE, ROUGE is from the [CommonGen GitHub repo](https://github.com/INK-USC/CommonGen).

    - Some commonly seen issues when installing the lib [\[link\]](https://docs.google.com/document/d/1BzOxaTx_ekV7UD07IALvhedn0T9uXNpT/edit?usp=sharing&ouid=111155601619122094904&rtpof=true&sd=true)


## Citation

```
@inproceedings{yu2022retrieval,
  title={Retrieval Augmentation for Commonsense Reasoning: A Unified Approach},
  author={Yu, Wenhao and Zhu, Chenguang and Zhang, Zhihan and Wang, Shuohang and Zhang, Zhuosheng and Fang, Yuwei and Jiang, Meng},
  booktitle={Proceedings of the 2022 Conference on Empirical Methods in Natural Language Processing (EMNLP)},
  year={2022}
}
```

Please kindly cite our paper if you find this paper and the codes helpful.
