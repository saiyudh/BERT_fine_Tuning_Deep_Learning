# BERT_fine_Tuning_Deep_Learning


The tutorial data set GLUE MRPC is classifying sentence pairs.
In the assignment, please use a data set to classify single sentences.
For example, GLUE itself has such data sets, like COLA or SST2, which are provided as TFDS.

You need to adapt the data preprocessing to be used for this task.
The suggested building of the model with bert.bert_models.classifier_model() is a very high-level abstraction.

Instead of using this function, take a pre-trained BERT encoder and connect it to a classification model yourself.
This way, you can understand better how the information flow from input through encoder to classifier.
