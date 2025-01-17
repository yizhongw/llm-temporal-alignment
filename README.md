# Set the Clock: Temporal Alignment of Pretrained Language Models

This repo contains the code and data for our paper [Set the Clock: Temporal Alignment of Pretrained Language Models](https://arxiv.org/abs/2402.16797), where we provide our benchmark and techniques of temporally aligning language models to a recent time.

<p align="center">
<img src="figures/TAQA.png" width="200" alt="TAQA">
</p>

We are currently working on reorganizing our code base for public release. Please check back in soon!

# News
- [2024/02/26] Our paper is now on arXiv! Check it out [here](https://arxiv.org/abs/2402.16797).
- [2024/02/27] We release our Temporal Alignment QA (TAQA) dataset on Hugging Face Datasets. Check it out [here](https://huggingface.co/datasets/ROIM/temporal-alignment-qa).

# Introduction

Our work investigates the *temporal chaos* of pretrained LMs and explores various methods to align their internal knowledge to a target time, which we call “temporal alignment.” In detail, we showed that pretrained LMs (e.g., LLaMa2), despite having a recent pretraining cutoff (e.g., 2022), mostly answer questions using earlier knowledge (e.g., in 2019). We have developed several methods, from prompting to finetuning, to align LMs to use their most recent knowledge when answering questions.

## Background
Language models (LMs) are trained on web text originating from many points in time and, in general, without any explicit temporal grounding. Since pretraining corpora are constructed over a wide time period, they inevitably contain outdated and contradictory information.

Previous studies have found that the temporal misalignment between LM pretraining and deployment has a significant impact on models’ performance, which motivates many studies on making model’s knowledge up-to-date.

## How temporal alignment works?
Based on our TAQA dataset, we can evaluate existing LMs' temporal alignment status by asking them time-sensitive questions and use each year's ground truth to measure the LM's F1 score over time, as shown below.

<p align="center">
<img src="figures/teaser_edited.png" alt="TAQA Data Construction Pipeline">
</p>

We propose a set of methods to temporally align LMs either to a target year or dynamically to recent years. Our methods include:
- **Time-aware Prompting**: We use prompts with time-sensitive few-shot examples and target year mention to guide the model to answer questions with recent knowledge.
- **Target-year Finetuning**: We finetune LMs on a subset of time-sensitive QA examples to align their knowledge to a target year, selected via the to-be-finetuned LM's answer correctness.
- **Temporal-adaptive Finetuning**: We finetune LMs on a set of time-sensitive QA examples to align their knowledge to recent years, with the specific year dynamically chosen based on the to-be-finetuned LM's internal knowledge.

## How was the TAQA dataset built?
Our TAQA dataset is automatically built through prompting GPT-4 based on tables with temporal information on Wikipedia pages. In detail, we parse the temporal mentions on Wikipedia tables, treating them as temporal qualifiers, and use other columns' name and corresponding values as prompts to ask GPT-4 for generating time-sensitive questions. Our data construction process ensures that the questions' answers will change multiple times over recent years (post 2000), which is a crucial property for evaluating temporal alignment in language models. Our data construction pipeline is shown below.

<p align="center">
<img src="figures/data_construction.png" alt="TAQA Data Construction Pipeline">
</p>

Our TAQA dataset is now available on Hugging Face Datasets. Check it out [here](https://huggingface.co/datasets/ROIM/temporal-alignment-qa).

# Setup

# Evaluation

# Licensing
This codebase and our TAQA dataset are released under Apache 2.0 License, as given in [LICENSE](https://github.com/yizhongw/llm-temporal-alignment/blob/main/LICENSE).

# Citation
If you use our code or TAQA dataset, please cite our work:
```
@misc{zhao2024set,
      title={Set the Clock: Temporal Alignment of Pretrained Language Models}, 
      author={Bowen Zhao and Zander Brumbaugh and Yizhong Wang and Hannaneh Hajishirzi and Noah A. Smith},
      year={2024},
      eprint={2402.16797},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```