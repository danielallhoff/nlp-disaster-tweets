# NLP Kaggle Challenge: Disaster Tweets
## Introduction
This is a repository for the Kaggle Challenge in "Natural Language Processing with Disaster Tweets". It consists of the prediction if the tweet mentions a real disaster or not.
Challenge link: https://www.kaggle.com/competitions/nlp-getting-started/data
## Experiment ideas
- Use a LLM as ChatGPT for NLP classification with specific prompts (e.g: few shot learning prompt)
- Use multiple features (not only the tweets text) as the keyword or the location of the tweet. Encode the keyword and the text separately and train a MLP. Dropout one or none of the two inputs (keyword and text) randomly. :white_check_mark:
- Make an ensemble of methods for improving results.
- Apply data augmentation to text with NLPAug. :white_check_mark:

  
## Results over ~10% validation set (from the training set)
| Experiment    | F1-Score | Precission | Recall
| ------------- | ------------- | ------------- | -------------
| Pretrained BERT + SVM with 768 components | 7.8% | 86.7% | 4.1% 
| Pretrained BERT + PCA (2 components) + SVM  | 1.2%  | 33.3% | 0.6% 
| Pretrained BERT + PCA (32 components) + SVM  | 61.5%  | 66.7% | 57.1%
| Pretrained BERT + PCA (64 components) + SVM  | 61.5%  | 68% | 56.2%
| Pretrained BERT + Random Forests | 61.4% | 69% | 55.2%
| Pretrained Bert + Attention Mask + Random forests | 69.2% | 75.6% | 63.8%
| Pretrained Bert + SMOTE | 71.29%		| 74.23%	| 68.57%
| Pretrained Bert cased + SMOTE | 71.2%		| 70.98%	| 71.43%
| Pretrained Bert + SMOTE + Random forests + Data augmentation | - | - | -
| Pretrained Bert + UnderSampling | 69.92%		| 69.38%	| 70.48%
| Pretrained Bert + SMOTE + KNNClassifier | 66.56%		| 60.51%	| 73.96%
| Pretrained Bert + extra keywords features | 69.21%		| 77.91%	| 62.25%
| Pretrained Bert + extra keywords features + MLP | 72.82%		| 78.86%	| 67.65%
**IN PROGRESS**

## Kaggle results
| Experiment    | F1-Score 
| ------------- | ------------- |
| Pretrained Bert cased + SMOTE + Data augmentation (NLPAug) + Random Forests | 0.74655 |
| Pretrained Bert + extra keywords features | 0.77719 |
| Pretrained Bert + extra keywords features + MLP | 0.78761 | 

## Links
- Torch transformers: https://pytorch.org/hub/huggingface_pytorch-transformers/
- Finetune transformers: https://huggingface.co/transformers/v4.2.2/custom_datasets.html
