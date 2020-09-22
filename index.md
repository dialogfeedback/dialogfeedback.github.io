---
layout: default
---

# About

Existing data-driven dialogue generation methods are mostly aimed to minimic the human response distribution. However, even human responses have different quality: some of them are popular, getting lots of upvoted, and some of them are less interesting or even offensive. So, we probably should optimize something else.

> Let's optimize expected human feedback, instead of just perplexity.

It is expensive to collect large-scale standard human evaluation data. Fortunately, there exists a huge amount of human feedback data (upvotes, number of replies, etc.) available on social platforms, such as Reddit. We leverage this data source and propose to train models to predict human feedback and help to build better chatbots.

# Tasks

Directly predicting the feedback is a hard task and there're many confounding factors, e.g. the timing of the comments and subreddits (topics and audience). Instead, we formulate the tasks as only scoring "comparable" pairs of responses of the same context, and predict which one has more feedback, in terms of number of upvotes👍 or replies💬.

The totally training dataset contains ~87 millions of samples.

|   Task  | Description  | Training size |
| :------:| :---------------------------------- | :---:|
| `updown`| which comment gets more upvotes👍?   | 40.7 M
| `width` | which comment gets more direct replies💬?   | 22.3 M |
| `depth` | which comment gets longer follow-up thread💬? | 25.1 M |

# Dataset

## Train

The training dataset is built from Reddit data from year 2011 to 2012


**Step 0.** Clone the repo.
```bash
git clone https://github.com/golsun/DialogRPT
cd DialogRPT
```

**Step 1.** Download the .bz2 files from this [third-party dump](https://files.pushshift.io/reddit/), including both [comments](https://files.pushshift.io/reddit/comments/) and [submissions](https://files.pushshift.io/reddit/submissions/). The following is the example command to download the first month, 2011-01. To reproduce the model training, please download all data for year 2011 and 2012, i.e., from 2011-01 to 2012-12.
```bash
mkdir "data/bz2"
wget https://files.pushshift.io/reddit/comments/RC_2011-01.bz2 -P data/bz2
wget https://files.pushshift.io/reddit/submissions/RS_2011-01.bz2 -P data/bz2
# TODO: repeat the above wget commands with months from `2011-01` to `2012-12`
```
**Step 2.** Read the .bz2 files and group items from the same subreddit and extract basic attributes and dialog trees.
```bash
python src/data.py bz2 2011
python src/data.py basic 2011
# TODO: repeat the above command with 2012
```
**Step 3.** Build training and testing data for different feedback signals. 
```bash
python src/data.py updown 2011
python src/data.py depth 2011
python src/data.py width 2011
# TODO: repeat the above command with 2012
```
The expected file structure in `data` folder is shown [here](./data.md).



## Test

The training dataset is built from Reddit data year 2013.

See [evaluation](https://github.com/golsun/DialogRPT#evaluation) for more details.


# Leaderboard

We evaluate the pairwise accuracy (a random guess is expected to have 0.5 accuracy)

|     | `updown` | `depth` | `width` |
| :-------------      | :------: |:------------: |:--------: |
| Length baseline |  0.531   | 0.543        | 0.591     | 
| Bag-of-words baseline |  0.571   | 0.583        | 0.596     | 
| Dialog ppl.         |  0.488   | 0.508         | 0.513     | 
| Reverse dialog ppl. |  0.560   | 0.557         | 0.571     | 
| [DialogRPT](https://github.com/golsun/DialogRPT) | **0.683** | **0.695**  | **0.752** | 

Want to submit a new results? Please [create an issue](https://github.com/golsun/DialogRPT/issues/new)!
