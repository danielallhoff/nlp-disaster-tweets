# NLP Kaggle Challenge: Disaster Tweets
## Introduction
This is a repository for the Kaggle Challenge in "Natural Language Processing with Disaster Tweets". It consists of the prediction if the tweet mentions a real disaster or not.

Challenge link: https://www.kaggle.com/competitions/nlp-getting-started/data

## Experiment ideas
- Use a LLM as ChatGPT for NLP classification with specific prompts (e.g: few shot learning prompt). :white_check_mark:
- Use multiple features (not only the tweets text) as the keyword or the location of the tweet. Encode the keyword and the text separately and train a MLP. Dropout one or none of the two inputs (keyword and text) randomly. :white_check_mark:
- Apply data augmentation to text with NLPAug. :white_check_mark:
- Make an ensemble of methods for improving results.
- Experiment with XGBoost.

## ChatGPT Prompts
Its is possible to use ChatGPT as a NLP classifier and work well on this task. Due to performance constrains, its is needed to test the prompts on a small validation set for making a final validation on the full testing set. Some prompts have been tested on the whole testing set. However, as stated, it is not feasible for testing multiple prompts.
### Initial few shot learning prompt:
```
You are a tweet analyst in order to monitor possible emergencies is posted online like fire, car or airplane accidents, earthquakes, tsunamis, homicides, bombing,
war, storm damage....etc.  It’s not always clear whether a tweet´s words are actually referring to a disaster that happened or is happening.
ANSWER ONLY WITH ONE INT VALUE: 1 (if the tweet speaks about a disaster) OR 0 (if not)!!!!!. DO NOT ANSWER WITH MORE THAN ONE INT VALUE!!!!
TEXT: On plus side LOOK AT THE SKY LAST NIGHT IT WAS ABLAZE.
DISASTER: 0.
TEXT: Our Deeds are the Reason of this #earthquake May ALLAH Forgive us all.
DISASTER:1.
TEXT: I'm on top of the hill and I can see a fire in the woods...
DISASTER: 1
TEXT: Jays rocking #MLB @JoeyBats19 just bombed one out of Rogers Centre. Play-offs r ahead for The #BlueJays - Bell Moseby and Barfield r back!
DISASTER: 0
TEXT: {query}
DISASTER: 
```

### Basic classification prompt without few shot learning:
```
You are a tweet analyst in order to monitor possible emergencies posted online like accidents (car accidents, airplane accidents, train wrecks or any type of accident),
natural disasters (for example: earthquakes, typhoon, tsunamis, storm damage, fire...etc), crimes (like homicides, killings, bombing, terrorism, casualties),
war, scandals....etc.  It’s not always clear whether a tweet´s words are actually referring to a disaster that happened or is happening.
ANSWER ONLY WITH ONE INT VALUE: 1 (if the tweet speaks about a disaster or emergency) OR 0 (if not)!!!!!.
DO NOT ANSWER WITH MORE THAN ONE INT VALUE!!!!
TEXT: {query}
YOUR RESPONSE:
```

## Initial test results over ~10% validation set (from the training set)
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
| Initial few shot learning prompt Chat GPT | 0.74624 |
| Basic classification prompt Chat GPT | 0.76463 |
| Finetuned BERT | 0.82653 |
| Finetuned BERT + extra keywords features (append text at the end) | 0.82286 |
| Finetuned BERT + extra keywords features (append text at the end) + Random Dropout | 0.8296 |

## Links
- Torch transformers: https://pytorch.org/hub/huggingface_pytorch-transformers/
- Finetune transformers: https://huggingface.co/transformers/v4.2.2/custom_datasets.html
