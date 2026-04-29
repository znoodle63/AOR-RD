# 📄 Explain Before Classify: Contrastive Rationale Distillation for Academic Opinion Recognition

This directory contains the dataset and related implementation details used in the following paper, including the prompt templates employed for rationale generation.

🔗 Paper: [Explain Before Classify: Contrastive Rationale Distillation for Academic Opinion Recognition](https://link.springer.com/chapter/10.1007/978-981-95-3453-1_21)



## 🔍 Overview

This work focuses on **academic opinion recognition** in scientific literature, particularly on identifying subjective expressions conveyed through implicit reasoning.

Instead of treating the task as a standard classification problem, we adopt an **explain-before-classify** paradigm:

- We first generate structured **rationales** to capture the underlying reasoning behind subjective expressions  
- These rationales are used as the primary supervision signal for training  
- The classification label is **deterministically derived from the rationale** via rule-based parsing, rather than being directly predicted  

To support this framework, we construct a dataset of sentences from ACL 2024 papers, where each instance is stored in **JSONL** format:

```json
{
  "text": "...",
  "label": 1,
  "rationale": "- Step 1: ...\n- Step 2: ...\n- Step 3: ..."
}
```

- `text`: input sentence  
- `label`: binary label (`1 = opinion`, `0 = non-opinion`)  
- `rationale`: structured explanation  


Rationales are generated using **GPT-4o** as the teacher model and follow a unified **three-step reasoning template**:

- Step 1: Identify the key expression [trigger word/phrase] in the sentence  
- Step 2: Analyze that this expression [action verb] [object] and reflects [subjectivity type]  
- Step 3: Therefore, determine whether the sentence expresses an academic opinion  

To further improve reasoning fidelity, we introduce a **contrastive learning strategy**:

- Counterfactual rationales with inverted logic are constructed  
- The model is trained to distinguish valid and flawed reasoning  
- This enhances robustness and interpretability of the learned representations  

Overall, this framework enables the model to jointly learn **classification and interpretable reasoning**, improving both prediction performance and explanation quality.
  

## ⚠️ Dataset Statistics

Due to an oversight, the statistics reported in the paper do not accurately reflect the final dataset, and **the statistics in the table below should be regarded as the authoritative reference**. The dataset contains **10,000 sentences** sampled from **ACL 2024 papers**.

| Label              | Train | Valid | Test | Total |
|-------------------|------:|------:|-----:|------:|
| Opinion (1)       | 3,779 | 490   | 482  | 4,751 |
| Non-opinion (0)   | 4,221 | 510   | 518  | 5,249 |
| **Total**         | 8,000 | 1,000 | 1,000 | 10,000 |


## 📌 Citation

If you find this dataset useful in your research, **please consider citing our paper**:

```bibtex
@inproceedings{zhang2025explain,
  title={Explain Before Classify: Contrastive Rationale Distillation for Academic Opinion Recognition},
  author={Mengting Zhang and Zhixiong Zhang and Yajiao Wang and Yang Li and Meng Wang},
  booktitle={International Conference on Advanced Data Mining and Applications},
  pages={311--325},
  year={2025},
  organization={Springer Nature Singapore}
}
```
