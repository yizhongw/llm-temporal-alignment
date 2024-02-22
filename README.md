# llm-temporal-alignment

This repo contains the code for our paper [llm-temporal-alignment](https://arxiv.org).
We are currently working on reorganizing our code base for public release alongside [our dataset](https://huggingface.co/datasets). Please check back in soon!

This work investigates the temporal chaos of pretrained LMs and explores various methods to align their internal knowledge to a target time, which we call “temporal alignment.” These methods all utilize [our Time-AwareQA (TAQA) dataset](https://huggingface.co/datasets). Based on this dataset, we showed that pretrained LMs (e.g., LLaMa2), despite having a recent pretraining cutoff (e.g., 2022), mostly answer questions using earlier knowledge (e.g., in 2019).
We have developed several methods, from prompting to finetuning, to align LMs to use their most recent knowledge when answering questions. Our results show that aligning LLaMa2 to the year 2022 can boost its performance by up to 62% relatively as measured by that year, even without mentioning time information explicitly, indicating the possibility of aligning models’ internal sense of time after pretraining. We also find that alignment to a historical time is also possible, with up to 2.8× the performance of the unaligned LM in 2010 if finetuning models to that year. 


# News

# Setup

# Evaluation

# Licensing

# Citation
