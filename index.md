---
layout: default
---

Existing data-driven dialogue generation methods are mostly aimed to minimic the human response distribution. However, even human responses have different quality: some of them are popular, getting lots of upvoted, and some of them are less interesting or even offensive. So, we probably should optimize or predict human feedback, instead of just perplexity.

> **Which dialogue response gets better human feedback?**

We leverage millions of Reddit human feedback data (number of upvotes👍 or replies💬) to formulate the following dialogue ranking tasks, to help building more engaging conversational AI. See our [EMNLP paper](https://arxiv.org/abs/2009.06978) or view [our project on Github](https://github.com/golsun/DialogRPT) for more details.


|   Task  | Description  | Training size |
| :------:| :---------------------------------- | :---:|
| `updown`| which comment gets more upvotes👍?   | 40.7 M
| `width` | which comment gets more direct replies💬?   | 22.3 M |
| `depth` | which comment gets longer follow-up thread💬? | 25.1 M |

# Dataset

### Downloading scripts

**Traning** dataset uses Reddit data from year 2011 to 2012. It can be built with [this script](https://github.com/golsun/DialogRPT/blob/master/data.sh), which downloads raw data from [a third party dump](https://files.pushshift.io/reddit) and extract comparable pairs of comments for classification tasks. 

```bash
git clone https://github.com/golsun/DialogRPT
cd DialogRPT
sh data.sh
```
See expected [data file structure](./data_structure.md)

**Testing** dataset uses Reddit data from year 2013. It can be downloaded [here](https://xiagnlp2.blob.core.windows.net/dialogrpt/test.zip) or use the command below
```
wget https://xiagnlp2.blob.core.windows.net/dialogrpt/test.zip
unzip test.zip
```
### Data description and example
Click [here](./data_example.md) to see examples and description of the data.


# Leaderboard

### Baselines
We evaluate the pairwise accuracy (a random guess is expected to have 0.5 accuracy)

|     | `updown` | `depth` | `width` |
| :-------------      | :------: |:------------: |:--------: |
| Length baseline |  0.531   | 0.543        | 0.591     | 
| Bag-of-words baseline |  0.571   | 0.583        | 0.596     | 
| Dialog ppl.         |  0.488   | 0.508         | 0.513     | 
| Reverse dialog ppl. |  0.560   | 0.557         | 0.571     | 
| [DialogRPT](https://github.com/golsun/DialogRPT) | **0.683** | **0.695**  | **0.752** | 

### Submit new results!
Want to submit a new results? Please [create an issue](https://github.com/golsun/DialogRPT/issues/new)!
