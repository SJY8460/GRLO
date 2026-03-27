# GRLO

Official code release for **GRLO: Towards Generalizable Reinforcement Learning in Open-Ended Environments from Zero**.

This repository contains the current GRLO training release, including:

- a `verl`-based training pipeline,
- a reference launch script for PPO-style training, and
- a 1,000-example open-ended prompt set for experimentation.

## Repository Contents

- `train.sh`: reference training launcher built on top of `verl`.
- `train.jsonl`: 1,000 open-ended training prompts in JSONL format.
- `verl/`: the RL training framework used by this project.

## Quick Start

1. Install the dependencies required by `verl`.
2. Set the training and validation file paths.
3. Replace the `<model>` placeholders in `train.sh` with your model path.
4. Launch training.

Example:

```bash
cd verl
pip install -e .

cd ..
export train_files=/path/to/train.jsonl
export val_files=/path/to/train.jsonl

# Edit train.sh first and replace <model> with your checkpoint or HF model path.
bash train.sh
```

## Data Format

`train.jsonl` stores chat-style training examples. Each record includes:

- the data source (not relevant),
- a user prompt,
- an ability tag,
- reward-model metadata, and
- auxiliary split/index information.

## Notes

- The training recipe in `train.sh` is provided as a starting point and may need to be adapted to your hardware, batch size, and model scale.
- For installation details and advanced configuration, please refer to the upstream `verl` documentation in [`verl/README.md`](./verl/README.md).

## Acknowledgment

GRLO is built on top of [verl](https://github.com/verl-project/verl), an efficient reinforcement learning framework for large language models.
