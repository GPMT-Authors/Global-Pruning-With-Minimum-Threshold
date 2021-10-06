# Global Magnitude Pruning With Minimum Threshold (GPMT)
This GitHub repository is the official repository for the paper "Global Magnitude Pruning With Minimum Threshold Is All We Need". 

## Set Up
0. Clone this repository.
1. Using `Python 3.6.9`, create a virtual environment `venv` with  `python -m venv myenv` and run `source myenv/bin/activate`.
2. Install requirements with `pip install -r requirements.txt` for `venv`.
3. Create a folder which has LabelSmoothing.py, prune_GP.py (or prune_GPMT.py), model_list.py, and the base model. 

## Training with GP and GPMT
To run the global magnitude pruning without minimum threshold (MT), run the prune_GP.py file. To run the global magnitude pruning with MT, run the prune_GPMT.py file. Finetuning code is included in both the files itself.

Note - you should change the base model's location and the dataset's location in the the prune_GP.py and prune_GPMT.py files before running them. 

To run the prune_GP.py file, run the command-
```
python3 prune_GP.py
```
To run the prune_GPMT.py file, run the command-
```
python3 prune_GPMT.py
```

### Dense Models:

This model is the base model that we used for our ResNet-50 on ImageNet experiments.

| Architecture | Parameters | Sparsity (%) | Top-1 Acc (%) | Model Links |
| ------------ | :--------: | :----------: | :-----------: | :---------: |
| Resnet-50        | 25.50M  | 0.00        | 77.04         | [Base Model](https://drive.google.com/file/d/1I7dxZD87-Ftav-BvIxqCWCWGWqYZFVK2/view?usp=sharing) |

### GP and GP+MT Pruned Models:

These models are the checkpoints of pruned Resnet-50 on ImageNet models by GP and GP+MT.

| Pruning Method | Sparsity (%) | Top-1 Acc (%) | Model Links |
| -------------- | :----------: | :-----------: | :---------: |
| GP             | 80           | 76.84         | [Pruned Model](https://drive.google.com/file/d/1bjZdFZiXhfh7fyXS-Mz3GOozAGl0yPDR/view?usp=sharing) |
| GP + 0.05% MT  | 80           | 76.81         | [Pruned Model](https://drive.google.com/file/d/1PkB80RD46vfsuWMxenEbjp5Jq6QXoV3M/view?usp=sharing) |
| GP             | 90           | 75.44         | [Pruned Model](https://drive.google.com/file/d/12V1SHhCxyG6QjrVEP-mT3iB33cLzBWNh/view?usp=sharing) |
| GP + 0.05% MT  | 90           | 75.42         | [Pruned Model](https://drive.google.com/file/d/1mTMHvF_-VNHNbpxFEU5mnfmdTNQoIhck/view?usp=sharing) |
| GP             | 95.30        | 71.63         | [Pruned Model](https://drive.google.com/file/d/1spUS0U2SgB_Dtc0k6pK7wQ24GUD4EnZt/view?usp=sharing) |
| GP + 0.005% MT | 95.30        | 71.55         | [Pruned Model](https://drive.google.com/file/d/1LySjDLF8ixmFQUS7NXC0BeN4Ss9AHOFV/view?usp=sharing) |
| GP             | 98.05        | 62.12         | [Pruned Model](https://drive.google.com/file/d/1K9326WN4xh4x_QoNqLo-T8AlQzBYn8zX/view?usp=sharing) |
| GP + 0.005% MT | 98.05        | 61.83         | [Pruned Model](https://drive.google.com/file/d/1T-_V8sWDJ4WU54n4qNL2V6OtFWZa0JTk/view?usp=sharing) |
