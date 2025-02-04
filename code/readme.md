# Code

This folder contains the scripts and  notebooks required to reproduce this study.
In order to reproduce the experiments, follow the order of the files listed below:

* `preprocessing.py` cleans the dataset from privacy-sensitive information (names, dates, times, locations, URLs, e-mail addresses). It pre-processes the dataset by applying lowercasing and stop words removal. It implements Binary Relevance problem transformation in order to convert the labels into 0 and 1. It conducts stratified data splitting in a ratio of 80-10-10 (train-validation-test).

* `statistics.ipynb` generates statistics regarding the full annotated dataset. It also includes code to inspect the label distribution in the split data (train-validation-test).

* `data_adaptation.py` undersamples the training dataset for the overrepresented main topics until they reach the average distribution, or can be used to pre-process the synthetic data generated by GPT-4.

* `SVMs_1step.py` trains a Support Vector Machines classifier, conducts hyper-parameter tuning and predicts the labels on the test set using TF-IDF feature representation. The script is designed for one-step classification, i.e. main topics and subtopics are learned and predicted in a single step. The script can be used with the original, undersampled or oversampled training data. The default for this script is the original training set.

* `SVMs_2step.py` trains a Support Vector Machines classifier, conducts hyper-parameter tuning and predicts the labels on the test set using TF-IDF feature representation. The script is designed for two-step classification, i.e. first the model is used to predict main topics, then to predict the corresponding subtopics using the output of the first phase. The script can be used with the original, undersampled or oversampled training data. The default for this script is the original training set.

* `BERT_1step.ipynb` fine-tunes a pre-trained BERT model on the training set, which has to be specified within the notebook by uncommenting certain parts. The default for this notebook is the original training set. The script is designed for one-step classification, i.e. main topics and subtopics are learned and predicted in a single step. The fine-tuned model is then saved to the models folder.
    * This script uses the helper functions stored in `utils.py`

* `BERT_2step.ipynb` fine-tunes a pre-trained BERT model on the training set, which has to be specified within the notebook by uncommenting certain parts. The default for this notebook is the original training set. The script is designed for two-step classification, i.e. first the model is used to predict main topics, then to predict the corresponding subtopics using the output of the first phase. The fine-tuned model is then saved to the models folder.
    * This script uses the helper functions stored in `utils.py`

* `error_analysis.py` allows you to inspect often confused topic labels, and can be used to look up a specific test instance (based on instance ID) to check its gold and predicted labels.
