# BERT_fine_Tuning_Deep_Learning


The tutorial data set GLUE MRPC is classifying sentence pairs.
In the assignment, please use a data set to classify single sentences.
For example, GLUE itself has such data sets, like COLA or SST2, which are provided as TFDS.

You need to adapt the data preprocessing to be used for this task.
The suggested building of the model with bert.bert_models.classifier_model() is a very high-level abstraction.

## Whether two sentences are semantically similar or not

Theoretically both tensors might not be necessary especially for single sentence as encoder can learn where actual sequence starts and padding begins instead of input mask. 


## What is a [CLS] token and what is it used for?

Token denotes start of the sentence or sequence. Used for classification.

## Which part of the BERT encoding is used for the classification?

Token is used for classification

## Does your answer match the output shape of the encoder?

Shape of the my answer doesn't match shape of output of encoder as encoder just outputs embeddings but Classifiers output matched my answer.

## Are the BERT encoder weights also fine-tuned to the task?

Yes, weights of encoder are finetuned while pretraining. 


#Connecting our own pretrained BERT
- After running above experiments connect a pretrained bert model to classifier and make it work on MRPC.




# Summary

- Load the pretrained encoder from tf hub and restore its weights from checkpoints. If you change the architecture like key and value sizes etc, you may need to pretrain model from scratch else weights can be restored.

- Download and preprocess the input dataset, During preprocessing use punctuation, space and wordpiece tokenizer.

- Download the pretrained vocabulary file which has word id to token mapping. This also has unknown tokens, special symbols etc. For chinese or non-english charatcers download separate vocabulary.

- You can also pretrain the vocabulary or make your own vocabulary file based on your domain and language.

- BPT tokenizer will split each word to separate tokens greedily, Add ## to let know that this token is a part of another word and not a word in itself. Each token is assigned a word id according to the vocabulary

- During encoding apply two types of masks, one to know where sequence stops and padding starts and another to differentiate between the sentences in the paddings(two sentence similarity classifier).

- Theoretically we may still need mask to know where input sequence stops and padding starts and we can don't need input_word_ids mask for single sentences, but when tried to encode this way we will get failure due to the architecture. So we need to include the mask.

- Create a manual classifier wrapping the transformer encoder, which has linear layer with vocab size as output options.

- Pretrain the entire architecture where transformer weights would be tuned very finely (much smaller than pretraining) and also classifier.

- Test on our random data


#Acknoledgements
OVGU teamwork students

