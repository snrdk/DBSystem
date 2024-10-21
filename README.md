# Term project (Lecture: Database system)
This repository aims to reproduce the findings of the paper "[Hate is the New Infodemic: A Topic-aware Modeling of Hate Speech Diffusion on Twitter](https://ieeexplore.ieee.org/abstract/document/9458789)"[1]. The model **_RETINA_** (**Ret**weeter **I**dentifier **N**etwork with Exogenous **A**ttention), a neural architecture to predict potential retweeters given a tweet, consists of two separate processes:
1) Spread as the hate generation
2) Retweet diffusion of hate

This model identifies multiple key factors that govern the dissemination of hate.


## Notes
* The authors' implementation of the code was only partially publicly available, and the dataset was not publicly available, so the code was reproduced as closely as possible to the paper.
* In the paper, the authors state that they used Twitter data from Indian users, but there is no explanation for this, so our work, we obtained and used a Twitter dataset suitable for the purpose of the proposed model: hate identification and retweet prediction.


## Setup

1. Clone this repository
2. Install the required packages:
```python
pip install -r requirements.txt```

3. Download the NLTK punkt tokenizer:
```python
import nltk
nltk.download('punkt')```

## Data

The project expects the following data files:

`annotations_metadata.csv`: Contains metadata about the annotated texts
`all_files/`: A directory containing text files with the content to be classified

## Features

