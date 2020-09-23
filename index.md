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

# 
Download the [**Dataset**](./data.md) and checkout the [**Leaderboard**](./leaderboard.md)