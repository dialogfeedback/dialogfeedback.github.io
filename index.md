---
layout: default
---

Existing data-driven dialogue generation methods are mostly aimed to minimic the human response distribution. However, even human responses have different quality: some of them are popular, getting lots of upvoted, and some of them are less interesting or even offensive. So, we probably should optimize something else.

> Let's optimize expected human feedback, instead of just perplexity.

It is expensive to collect large-scale standard human evaluation data. Fortunately, there exists a huge amount of human feedback data (upvotes, number of replies, etc.) available on social platforms, such as Reddit. We leverage this data source and propose to train models to predict human feedback and help to build better chatbots.

# Dataset

Directly predicting the feedback is a hard task and there're many confounding factors, e.g. the timing of the comments and subreddits (topics and audience). Instead, we formulate the tasks as only scoring "comparable" pairs of responses of the same context.

## Train

The training dataset is built from Reddit data from year 2011 to 2012

|   Task  | Description | Size (millions) |
| :------:| :---------------------------------- |:---: |
| `updown`|  which comment gets more upvotes?   | 40.7 | 
| `width` |  which comment gets more direct replies?   | 22.3 | 
| `depth` | which comment gets longer follow-up thread? | 25.1 | 

See [data extraction](./data.md) for more details.

## Test

The training dataset is built from Reddit data year 2013.

See [evaluation](https://github.com/golsun/DialogRPT#evaluation) for more details.

# Leaderboard

|     | `updown` | `depth` | `width` |
| :-------------      | :------: |:------------: |:--------: |
| Length baseline |  0.531   | 0.543        | 0.591     | 
| Bag-of-words baseline |  0.571   | 0.583        | 0.596     | 
| Dialog ppl.         |  0.488   | 0.508         | 0.513     | 
| Reverse dialog ppl. |  0.560   | 0.557         | 0.571     | 
| [DialogRPT](https://github.com/golsun/DialogRPT) | **0.683** | **0.695**  | **0.752** | 
