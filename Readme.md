## Introduction

This is the source code of "Cross-Modal Attention with Semantic Consistence for Image-Text Matching", implemented by [Tan Wang](https://github.com/Wangt-CN). 

Xing Xu, Tan Wang, Yang Yang, Lin Zuo, Fumin Shen and Heng Tao Shen. “Cross-Modal Attention with Semantic Consistence for Image-Text Matching”. IEEE Transactions on Neural Networks and Learning Systems (TNNLS), 2020.


## Cross-Modal Attention with Semantic Consistence for Image-Text Matching

The proposed CASC is a joint framework that performs cross-modal attention for local alignment and multi-label prediction for global semantic consistence. It directly extracts semantic labels from available sentence corpus without additional labor cost, which further provides a global similarity constraint for the aggregated region-word similarity obtained by the local alignment.

![framework](https://github.com/Wangt-CN/Code_CASC/blob/master/fig/framework-xing.jpg)




## Proposed Model (CASC)

- Cross-modal Representation Learning
  - Image Representation
  - Sentence Representation
  
- Cross-modal Attention
  - I2T Attention
  - T2I Attention
  - Local Alignment with Cross-modal Attention
  
- Global Semantic Consistence
  - Semantic Labels Extraction
  - Semantic Consistence Preservation

   
## Motivation

![example](https://github.com/Wangt-CN/Code_CASC/blob/master/fig/example_fig1.jpg)

A typical example of the sentence retrieval results obtained by the latest fine-grained matching method SCAN [1] and our proposed CASC. The top 3 retrieved sentences of the two methods are respectively presented in the two rectangles. In particular, the most related semantic labels with their similarity scores to the image can also be predicted by our CASC.



## Retrieval Examples

![example](https://github.com/Wangt-CN/Code_CASC/blob/master/fig/vis_examples.jpg)




## Data Download

Download the dataset files and pre-trained models. We use splits produced by [Andrej Karpathy](http://cs.stanford.edu/people/karpathy/deepimagesent/). The raw images can be downloaded from from their original sources [here](http://nlp.cs.illinois.edu/HockenmaierGroup/Framing_Image_Description/KCCA.html), [here](http://shannon.cs.illinois.edu/DenotationGraph/) and [here](http://mscoco.org/).

The precomputed image features of MS-COCO are from [here](https://github.com/peteanderson80/bottom-up-attention). The precomputed image features of Flickr30K are extracted from the raw Flickr30K images using the bottom-up attention model from [here](https://github.com/peteanderson80/bottom-up-attention). All the data needed for reproducing the experiments in the paper, including image features and vocabularies, can be downloaded from:

```
wget https://scanproject.blob.core.windows.net/scan-data/data.zip
wget https://scanproject.blob.core.windows.net/scan-data/vocab.zip
```

We refer to the path of extracted files for `data.zip` as `$DATA_PATH` and files for `vocab.zip` to `./vocab` directory. Alternatively, you can also run vocab.py to produce vocabulary files. For example,

```
python vocab.py --data_path data --data_name f30k_precomp
python vocab.py --data_path data --data_name coco_precomp
```




## Usage

- Run vocab.py pre-process training images and captions
- Modify the parameters in train.py
- Run train.py
- Run evaluation_.py to evaluate the R@K of the model 



## Results

![example](https://github.com/Wangt-CN/Code_CASC/blob/master/fig/table.png)
