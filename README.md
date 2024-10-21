# Term project (Lecture: Database system)
This repository aims to reproduce the findings of the paper "[Hate is the New Infodemic: A Topic-aware Modeling of Hate Speech Diffusion on Twitter](https://ieeexplore.ieee.org/abstract/document/9458789)"[1]. The model **_RETINA_** (**Ret**weeter **I**dentifier **N**etwork with Exogenous **A**ttention), a neural architecture to predict potential retweeters given a tweet, consists of two separate processes:
1) Spread as the hate generation
2) Retweet diffusion of hate

This model identifies multiple key factors that govern the dissemination of hate.


## Notes
* The authors' implementation of the code was only partially publicly available, and the dataset was not publicly available, so the code was reproduced as closely as possible to the paper.
* In the paper, the authors state that they used Twitter data from Indian users, but there is no explanation for this, so our work, we obtained and used an another dataset suitable for the purpose of the proposed model: hate identification and retweet prediction (See below for a description of the datasets used).
* The neural network model is defined in the `StaticModel_noexo` function.
* The notebook uses TensorFlow for the neural network implementation.
* Sklearn is used for logistic regression and decision tree classifiers.
* Gensim is used for Doc2Vec implementation.


## Setup

1. Clone this repository
2. Install the required packages:
```python
pip install -r requirements.txt
```

3. Download the NLTK punkt tokenizer:
```python
import nltk
nltk.download('punkt')
```

## Dataset
The project expects the following data files:

`annotations_metadata.csv`: Contains metadata about the annotated texts from Hate speech dataset from white supremacist forums.    
You can download this file from [Here](https://github.com/sara-02/hate-speech-dataset).  

This files contain text extracted from Stormfront, a white supremacist forum, and was used in the paper "[Hate speech dataset from a white supremacy forum](https://arxiv.org/abs/1809.04444)"[2]. The dataset was created by randomly sampling forum posts from several sub-forums and separating them into sentences. These sentences were manually labelled according to whether they contain hate speech according to specific annotation guidelines.

`all_files`: A directory containing text files with the content to be classified. The file name is formatted as commentID_sentenceNumber.txt, so the files that share the same number before the underscore pertain to the same comment.  


## Features
* Text vectorization using Doc2Vec
* User hate ratio calculation
* Neural network model for classification
* Comparison with traditional machine learning models (Logistic Regression, Decision Trees)


## Usage
Run the Jupyter notebook `hate_diffusion_prediction.ipynb` to:  

1. Load and preprocess the data
2. Train the Doc2Vec model
3. Train and evaluate the neural network model
4. Compare performance with logistic regression and decision tree classifiers


## Model Performance
The notebook includes code to evaluate the models using accuracy and AUC metrics.


## References
[1] Masud, S., Dutta, S., Makkar, S., Jain, C., Goyal, V., Das, A., & Chakraborty, T. (2021, April). Hate is the new infodemic: A topic-aware modeling of hate speech diffusion on twitter. In 2021 IEEE 37th International Conference on Data Engineering (ICDE) (pp. 504-515). IEEE.  
[2] De Gibert, O., Perez, N., García-Pablos, A., & Cuadros, M. (2018). Hate speech dataset from a white supremacy forum. arXiv preprint arXiv:1809.04444.

