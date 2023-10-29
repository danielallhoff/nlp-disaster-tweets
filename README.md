# NLP Kaggle Challenge: Disaster Tweets
## Introduction
This is a repository for the Kaggle Challenge in "Natural Language Processing with Disaster Tweets". It consists of the prediction if the tweet mentions a real disaster or not.
Challenge link: https://www.kaggle.com/competitions/nlp-getting-started/data
## Experiment ideas
- Use a LLM as ChatGPT for NLP classification with specific prompts (e.g: few shot learning prompt)
- Use multiple features (not only the tweets text) as the keyword or the location of the tweet. Encode the keyword and the text separately and train a MLP. Dropout one or none of the two inputs (keyword and text) randomly.
- Make an ensemble of methods for improving results.
- Apply data augmentation for more variety.
  
## Results over validation set
| Experiment    | F1-Score | Precission | Recall
| ------------- | ------------- | ------------- | -------------
| Pretrained BERT + SVM with 768 components | 7.8% | 86.7% | 4.1% 
| Pretrained BERT + Random Forests | 61.4% | 69% | 55.2%
| Pretrained BERT + PCA (2 components) + SVM  | 1.2%  | 33.3% | 0.6% 
| Pretrained BERT + PCA (32 components) + SVM  | 61.5%  | 66.7% | 57.1%
| Pretrained BERT + PCA (64 components) + SVM  | 61.5%  | 68% | 56.2%

**IN PROGRESS**

## Kaggle results
**IN PROGRESS**

## Links
- Torch transformers: https://pytorch.org/hub/huggingface_pytorch-transformers/
- Finetune transformers: https://huggingface.co/transformers/v4.2.2/custom_datasets.html
