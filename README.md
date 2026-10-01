# Bangla Text Dataset for Online Harassment Detection

**44,001 real Facebook comments written in Bangla (Bengali), each labelled by whether it is harassment and, if so, what kind.**

> ⚠️ **Content warning:** This dataset contains real social media comments, including sexual, threatening, religiously offensive and abusive language. It is shared only to help researchers build tools that detect and reduce online harassment.

---

## Why this dataset exists

Bangla is the seventh most spoken language in the world, and more and more Bangla speakers are online every year. With that growth has come a lot of online harassment (cyberbullying) in Bangla, especially in the comment sections of public figures' posts.

Computers can be trained to spot harassment automatically, but only if they have examples to learn from. Plenty of such examples exist for English. For Bangla there were very few. We built this dataset to fill that gap.

## What we did

1. **Collected comments.** We gathered 44,001 comments that people left under public Facebook posts by celebrities, actors, singers, politicians, government officials and athletes.
2. **Labelled them.** With help from experts, and only after the annotators agreed on a label, each comment was marked as either *not bully* or one of four types of harassment.
3. **Explored the data.** We studied who receives the most harassment, which kinds are most common, and how these patterns differ. That analysis is in our [dataset paper](https://arxiv.org/abs/2102.02478).
4. **Built detection models.** We used the dataset to train deep learning models that read a Bangla comment and decide whether it is bullying, and what kind. These are described in our [model paper](https://arxiv.org/abs/2106.04506).
   - Bullying or not (two choices): **87.91% accuracy**
   - Which of the five classes (multi-class): **85% accuracy**

## What's in the file

All of the data is in a single file, [`dataset.csv`](dataset.csv) (UTF-8, about 12 MB). Each row is one comment.

| Column | What it means | Example |
|---|---|---|
| `comment` | The comment text, mostly in Bangla script | `ক্যাপ্টেন অফ বাংলাদেশ` |
| `Category` | The kind of public figure whose post was commented on | `Sports` |
| `Gender` | The gender of that public figure | `Male` |
| `comment react number` | How many reactions (likes, etc.) the comment received | `0` |
| `label` | The harassment label (see below) | `not bully` |

### The labels

| Label | Meaning | Comments | Share |
|---|---|---:|---:|
| `not bully` | A normal, non-abusive comment | 15,340 | 34.9% |
| `troll` | Mockery, insults or ridicule meant to provoke | 10,462 | 23.8% |
| `sexual` | Sexual harassment or sexually explicit abuse | 8,928 | 20.3% |
| `religious` | Attacks or abuse based on religion | 7,577 | 17.2% |
| `threat` | Threats of harm or violence | 1,694 | 3.9% |

About two thirds of the comments (65%) are some form of harassment.

### Who the comments were aimed at

| Category | Comments | | Gender | Comments |
|---|---:|---|---|---:|
| Actor | 26,951 | | Female | 29,950 |
| Social (social media figures) | 9,375 | | Male | 14,051 |
| Singer | 2,981 | | | |
| Politician | 2,633 | | | |
| Sports | 2,061 | | | |

### Quick start (Python)

```python
import pandas as pd

df = pd.read_csv("dataset.csv")
print(df["label"].value_counts())
```

Three rows have an empty `comment react number`. Fill or drop them if your analysis uses that column.

## What you can use it for

- Training models to flag abusive Bangla comments automatically
- Telling *types* of harassment apart (sexual, threatening, religious, trolling)
- Studying who gets harassed online, for example by gender or profession
- Building moderation tools for Bangla-speaking communities

## Papers

If you use this dataset, please cite the paper(s) that fit your work.

**1. Bangla Text Dataset and Exploratory Analysis for Online Harassment Detection**
Md Faisal Ahmed, Zalish Mahmud, Zarin Tasnim Biash, Ahmed Ann Noor Ryen, Arman Hossain, Faisal Bin Ashraf
arXiv:2102.02478 · [Read the paper](https://arxiv.org/abs/2102.02478)
*Describes the dataset and our analysis of it.*

**2. Cyberbullying Detection Using Deep Neural Network from Social Media Comments in Bangla Language**
Md Faisal Ahmed, Zalish Mahmud, Zarin Tasnim Biash, Ahmed Ann Noor Ryen, Arman Hossain, Faisal Bin Ashraf
arXiv:2106.04506 · [Read the paper](https://arxiv.org/abs/2106.04506)
*Describes the deep learning models trained on this dataset.*

```bibtex
@misc{ahmed2021bangla,
  title         = {Bangla Text Dataset and Exploratory Analysis for Online Harassment Detection},
  author        = {Ahmed, Md Faisal and Mahmud, Zalish and Biash, Zarin Tasnim and Ryen, Ahmed Ann Noor and Hossain, Arman and Ashraf, Faisal Bin},
  year          = {2021},
  eprint        = {2102.02478},
  archivePrefix = {arXiv}
}

@misc{ahmed2021cyberbullying,
  title         = {Cyberbullying Detection Using Deep Neural Network from Social Media Comments in Bangla Language},
  author        = {Ahmed, Md Faisal and Mahmud, Zalish and Biash, Zarin Tasnim and Ryen, Ahmed Ann Noor and Hossain, Arman and Ashraf, Faisal Bin},
  year          = {2021},
  eprint        = {2106.04506},
  archivePrefix = {arXiv}
}
```

The dataset is also archived on Mendeley Data: <https://data.mendeley.com/datasets/9xjx8twk8p>

## Responsible use

These are real comments written by real people. Please use the data only for research and for building tools that make online spaces safer. Do not use it to target, profile or re-identify individuals.

## License

Released under the [MIT License](LICENSE).
