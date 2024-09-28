# CaptionCraft: Leveraging Transformers For Image Captioning

### Introduction

This repository contains code and model checkpoints for CaptionCraft, an image captioning application that leverages Transformer models to generate intelligent and detailed captions for images. 
The model used is a combination of Vision Transformer (ViT-Base-Patch16-224) for extracting dense, high-quality features from images, and GPT2 (Generative Pre-trained Transformer) for generating
comprehensive and contextually-rich captions given the extracted features

### Dataset

The dataset used is Flickr 8K Dataset. The dataset contains around 8k images, each image paired with 5 different captions which provide clear descriptions of the salient entities and event. The 
images have been manually selected to contain various situations and scenarios.

The dataset can be found here at: https://www.kaggle.com/datasets/adityajn105/flickr8k/data

### Models 

1) Encoder: ViT-Base-Patch16-224

<img src = "https://production-media.paperswithcode.com/methods/Screen_Shot_2021-01-26_at_9.43.31_PM_uI4jjMq.png">

<br />The Vision Transformer, or ViT, is a model for image classification that employs a Transformer-like architecture over patches of the image. An image is split into fixed-size patches, each of them are then linearly embedded, position embeddings are added, and the resulting sequence of vectors is fed to a standard Transformer encoder. In order to perform classification, the standard approach of adding an extra learnable “classification token” to the sequence is used.
<br />

2) Decoder: GPT2

![Structure-of-the-applied-GPT-2-medium-architecture](https://github.com/user-attachments/assets/a0254faf-688a-4cee-8495-d601148ccc6f)


<br />GPT-2 is a Transformer model pretrained on a very large corpus of English data in a self-supervised fashion. Inputs are sequences of continuous text of a certain length and the targets are the same sequence, shifted one token to the right. The model uses internally a mask-mechanism to make sure the predictions for a particular tojeb only uses the previous token inputs but not the future tokens. This way, the model learns an inner representation of the English language that can then be used to extract features useful for downstream tasks. The model is best at what it was pretrained for however, which is generating texts from a prompt.

### Metric

The metric used is ROUGE-L. ROUGE(Recall-Oriented Understudy for Gisting Evaluation) is a set of metrics used for tasks that involve sentences as outputs, like Machine Translation, Automatic Summarization,
Image Captioning, .etc. ROUGE-L measures the number of unigrams in the longest common subsequence (LCS) between the candidate and the reference captions, relative to the number of unigrams in both. This is
based on the fact that a longer LCS implies more similarity between the two captions, especially for words which are not consecutive.

More details about the metric can be found at: https://medium.com/nlplanet/two-minutes-nlp-learn-the-rouge-metric-by-examples-f179cc285499

### Libraries Used

1) Pytorch for handling tensors
2) ImageIO for loading and pre-processing images
3) Torchvision for transforms and dataset creation
4) Transformers for loading ViT, GPT2 models as well as Seq2SeqTrainer for end-to-end fine-tuning





