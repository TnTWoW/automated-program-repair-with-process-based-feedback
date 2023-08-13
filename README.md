## Automated Program Repair with Process-based Feedback

This is the official code for the paper **[Automated Program Repair with Process-based Feedback]()** 

### Contents:
- [Overview](#overview)
- [Installation](#installation)
- [Datasets](#datasets)
- [Usage](#usage)

## Overview

* Humans make multiple revisions when writing programs, while LLMs cannot receive feedback from compiler and test cases to optimize its repair policies automatically. We are exploring how to ensure small-scale LLM still outperform through process supervision and feedback.

* During training, we develop a reward model that serves as a critic, providing feedback for the fine-tuned LM’s action, progressively optimizing its policy.

* During inference, we require the LM to generate solutions iteratively until the repair effect no longer improves or hits the maximum step limit.

## Installation

The code requires some dependencies as specified in `requirements.txt`. Please follow the relevant libraries to install or run: 

`pip install -r requirements.txt`

## Datasets

We establish a multi-step program repair dataset based on [Project_CodeNet](https://github.com/IBM/Project_CodeNet), which we call CodeNet4Repair. It include comprehensive test cases, problem descriptions, and detailed repair steps.

The dataset are available here:

```
https://huggingface.co/datasets/TnT/Multi_CodeNet4Repair
```

## Usage

```python
from transformers import AutoTokenizer
import transformers
tokenizer = AutoTokenizer.from_pretrained(model)
pipeline = transformers.pipeline(
    "text-generation",
    model=model,
    torch_dtype=torch.float32,
    device_map="auto",
)
```