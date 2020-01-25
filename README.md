# Training BERT for Named Entity Recognition in Slovak language
In this experiment, we will be training a state-of-the-art Natural Language Understanding model [BERT](https://arxiv.org/abs/1810.04805.) on manually annotated corpus of Court decisions from https://ru.justice.sk/ data using Google Cloud infrastructure.

This guide covers all stages of the procedure, including:

1. Setting up the training environment
2. Getting the data
3. Preparing models
4. Training model on cloud GPU
5. Evaluate the results
6. Uploading model to GCS (optional)
7. Serving BERT model for NER as a Service
8. Testing the services

For persistent storage of training data and model, you will require a Google Cloud Storage bucket. 
Please follow the [Google Cloud TPU quickstart](https://cloud.google.com/tpu/docs/quickstart) to create a GCP account and GCS bucket. New Google Cloud users have [$300 free credit](https://cloud.google.com/free/) to get started with any GCP product.
This document is based on document from: https://towardsdatascience.com/pre-training-bert-from-scratch-with-cloud-tpu-6e2f71028379

Start with the Google colab: https://colab.research.google.com/github/Ardevop-sk/sk-bert-ner/blob/master/SK_NER_BERT.ipynb

## Dataset:
NumDocs: 710

Train: 510

Dev: 100

Test: 100

```
2020-01-25 22:31:04,674 :  -------------------------
2020-01-25 22:31:04,675 :  Entity Organizacia
2020-01-25 22:31:04,676 :  TP: 420 FP: 5 FN: 10
2020-01-25 22:31:04,677 :  Precision: 0.9882352941176471
2020-01-25 22:31:04,678 :  Recall: 0.9767441860465116
2020-01-25 22:31:04,679 :  F1: 0.9824561403508771
2020-01-25 22:31:04,679 :  -------------------------
2020-01-25 22:31:04,680 :  Entity ICO
2020-01-25 22:31:04,682 :  TP: 75 FP: 0 FN: 0
2020-01-25 22:31:04,682 :  Precision: 1.0
2020-01-25 22:31:04,684 :  Recall: 1.0
2020-01-25 22:31:04,686 :  F1: 1.0
2020-01-25 22:31:04,687 :  -------------------------
2020-01-25 22:31:04,688 :  Entity O
2020-01-25 22:31:04,690 :  TP: 60611 FP: 0 FN: 0
2020-01-25 22:31:04,690 :  Precision: 1.0
2020-01-25 22:31:04,692 :  Recall: 1.0
2020-01-25 22:31:04,694 :  F1: 1.0
2020-01-25 22:31:04,695 :  -------------------------
2020-01-25 22:31:04,696 :  Entity Sud
2020-01-25 22:31:04,698 :  TP: 356 FP: 54 FN: 0
2020-01-25 22:31:04,698 :  Precision: 0.8682926829268293
2020-01-25 22:31:04,700 :  Recall: 1.0
2020-01-25 22:31:04,702 :  F1: 0.9295039164490863
2020-01-25 22:31:04,703 :  -------------------------
2020-01-25 22:31:04,704 :  Entity Narodenie
2020-01-25 22:31:04,706 :  TP: 124 FP: 0 FN: 0
2020-01-25 22:31:04,707 :  Precision: 1.0
2020-01-25 22:31:04,711 :  Recall: 1.0
2020-01-25 22:31:04,717 :  F1: 1.0
2020-01-25 22:31:04,728 :  -------------------------
2020-01-25 22:31:04,735 :  Entity Adresa
2020-01-25 22:31:04,737 :  TP: 1291 FP: 2 FN: 28
2020-01-25 22:31:04,739 :  Precision: 0.9984532095901005
2020-01-25 22:31:04,741 :  Recall: 0.9787717968157695
2020-01-25 22:31:04,744 :  F1: 0.9885145482388974
2020-01-25 22:31:04,747 :  -------------------------
2020-01-25 22:31:04,750 :  Entity Osoba
2020-01-25 22:31:04,753 :  TP: 485 FP: 0 FN: 3
2020-01-25 22:31:04,757 :  Precision: 1.0
2020-01-25 22:31:04,759 :  Recall: 0.9938524590163934
2020-01-25 22:31:04,762 :  F1: 0.9969167523124358
```
