---
layout: default
---

Existing data-driven dialogue generation methods are mostly aimed to minimic the human response distribution. However, even human responses have different quality: some of them are popular, getting lots of upvoted, and some of them are less interesting or even offensive. So, we probably should optimize something else.

> **Let's optimize expected human feedback, instead of just perplexity.**

It is expensive to collect large-scale standard human evaluation data. Fortunately, there exists a huge amount of human feedback data (upvotes, number of replies, etc.) available on social platforms, such as Reddit. We leverage this data source and propose to train models to predict human feedback and help to build better chatbots.

Directly predicting the feedback is a hard task and there're many confounding factors, e.g. the timing of the comments and subreddits (topics and audience). Instead, we formulate the tasks as only focusing on "comparable" pairs of responses of the same context, and predict which one has more feedback, in terms of number of upvotes👍 or replies💬. See our [EMNLP paper](https://arxiv.org/abs/2009.06978) for details.

|   Task  | Description  | 
| :------:| :---------------------------------- | 
| `updown`| which comment gets more upvotes👍?   |
| `width` | which comment gets more direct replies💬?   |
| `depth` | which comment gets longer follow-up thread💬? | 

# Dataset

See [data](./data.md) for instructions to build dataset, dataset statistics and examples.


# Leaderboard

see [baseline performance](./leaderboard.md)

Want to submit a new results? Please [create an issue](https://github.com/golsun/DialogRPT/issues/new)!
