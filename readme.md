# ReDPJ
This repository contains official implementation of our paper "Reasoning as a Weapon: Dual-Path Jailbreak Attack on Large Language Models".

[![arXiv: paper](https://img.shields.io/badge/arXiv-paper-red.svg)](https://arxiv.org/abs/2407.16205)
![Jailbreak Attacks](https://img.shields.io/badge/Jailbreak-Attacks-yellow.svg?style=plastic)
![Large Language Models](https://img.shields.io/badge/LargeLanguage-Models-green.svg?style=plastic)
[![license: MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Please feel free to contact linshizjsu@gmail.com if you have any questions.

## Table of Contents

- [Overview](#overview)
- [Argument Specification](#argument-specification)
- [Quick Start](#quick-start)


## Overview

This repository shares the code of our latest work on LLMs jailbreaking. In this work:
    
- We investigate a novel jailbreak attack paradigm that transitions from input-level obfuscation to reasoning-level manipulation, unveiling an overlooked attack surface inherently in the chain-of-thought reasoning trajectory of LLMs.
- We present ReDPJ, a reasoning-guided dual-path jailbreak attack that steers the model's reasoning chain towards producing harmful content. ReDPJ introduces dual-modality attack paths, effectively exposing the intrinsic vulnerabilities within the textual and visual reasoning processes of LLMs.
- We conduct extensive experiments on diverse LLMs, demonstrating ReDPJ’s impressive performance in terms of attack effectiveness, efficiency, and transferability. Additionally, we validate the effectiveness of the key components in ReDPJ and analyze the reasons behind the success of attack.

<p align="center">
  <img src="ABJ.png" width="900"/>
</p>


## Argument Specification
  
- `target_model`: The name of target model.

- `assist_model`: The name of assist model.

- `judge_model`: The name of judge model.
  
- `max_attack_rounds`: Number of attack iteration rounds, default is `3`.

- `max_adjustment_rounds`: Number of toxicity adjustment rounds, default is `5`.

- `target_model_cuda_id`: Number of the GPU for target model, default is `cuda:0`.

- `assist_model_cuda_id`: Number of the GPU for assist model, default is `cuda:1`.

- `judge_model_cuda_id`: Number of the GPU for judge model, default is `cuda:2`.

  
## Quick Start

Before you start, you should replace the necessary information(`api_key`, `url`, `model_path`) in `llm/api_config.py` and `llm/llm_model.py`.


1. Clone this repository:

   ```sh
   git clone https://github.com/theshi-1128/ReDPJ.git
   ```

2. Build environment:

   ```sh
   cd ReDPJ
   conda create -n ReDPJ python==3.11
   conda activate ReDPJ
   pip install -r requirements.txt
   ```

3. Run ReDPJ:

     ```sh
     python ReDPJ.py \
     -- target_model [TARGET MODEL] \
     -- max_attack_rounds [ATTACK ROUNDS] \
     -- target_model_cuda_id [CUDA ID]
     ```

    For example, to run `ReDPJ` with `gpt-4o-2024-11-20` as the target model on `CUDA:0` for `3` rounds, run
  
     ```sh
     python ReDPJ.py \
     -- target_model gpt4o \
     -- max_attack_rounds 3 \
     -- target_model_cuda_id cuda:1
     ```



