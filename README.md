# Training BERT for Named Entity Recognition in Slovak language
In this experiment, we will be training a state-of-the-art Natural Language Understanding model [BERT](https://arxiv.org/abs/1810.04805.) on manually annotated korpus of Court decisions from https://ru.justice.sk/ data using Google Cloud infrastructure.

This guide covers all stages of the procedure, including:

1. Setting up the training environment
2. Getting the data
3. Preparing models
4. Training model on cloud GPU
5. Downloading model to GCS
6. Serving BERT model for NER
7. Testing the services

For persistent storage of training data and model, you will require a Google Cloud Storage bucket. 
Please follow the [Google Cloud TPU quickstart](https://cloud.google.com/tpu/docs/quickstart) to create a GCP account and GCS bucket. New Google Cloud users have [$300 free credit](https://cloud.google.com/free/) to get started with any GCP product.
This document is based on document from: https://towardsdatascience.com/pre-training-bert-from-scratch-with-cloud-tpu-6e2f71028379

Start with the Google colab: https://colab.research.google.com/github/Ardevop-sk/sk-bert-ner/blob/master/SK_NER_BERT.ipynb
