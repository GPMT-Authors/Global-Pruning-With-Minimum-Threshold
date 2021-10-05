# Global-Magnitude-Pruning-With-Minimum-Threshold-MT-
This GitHub repository is the official repository for the paper "Global Magnitude Pruning With Minimum Threshold Is All We Need". 

## Set Up
0. Clone this repository.
1. Using `Python 3.6.9`, create a virtual environment `venv` with  `python -m venv myenv` and run `source myenv/bin/activate`.
2. Install requirements with `pip install -r requirements.txt` for `venv`.
3. Create a folder which has LabelSmoothing.py, prune_GP.py (or prune_GPMT.py), model_list.py, and the base model. 

## Training with GP and GPMT
To run the global magnitude pruning without minimum threshold (MT), run the prune_GP.py file. To run the global magnitude pruning with MT, run the prune_GPMT.py file. 

Each run of the prune_MT.py file will create:

0. prune_log.csv
1. prunedmodel.pth.tar 
2. weight_mask.npy
3. a csv file compiling the logs of each training epoch
4. best model checkpoints after each epoch

Each run of the prune_GPMT.py file will create:

0. prune_log.csv (prune logs without MT)
1. layer_sparsities.csv
2. prune_refined_log.csv (prune logs with MT)
3. prunedmodel.pth.tar (pruned base model)
4. weight_mask.npy
5. a csv file compiling the logs of each training epoch
6. best model checkpoints after each epoch

Which by default, all of them will be created in the same directory as the code files. 

The arguments that you could change are:

0. --epochs (for number of total epochs to train)
1. --batch-size (total batch size for all GPUs)
2. --lr (initial learning rate)
3. --momentum
4. --weight-decay
5. --smoothing
6. --sparsity
7. --min-threshold (MT, for prune_GPMT.py only)

Note that you should change the base model's location and the dataset's location by yourself by editing the prune_GP.py and prune_GPMT.py files before running them. Also, if you want to change the scheduler, you should change them by yourself. The formula that we used are: 

0. cosine scheduler : 0.5 * (1 + np.cos(np.pi * epoch / total_epoch)) * initial_lr
1. linear scheduler : initial_lr - epoch / total_epoch * initial_lr

### Dense Models:

These models are the base models that we used for our experiments. The model definition used are in the model_list.py file or the original model definition made by its authors. 

| Architecture | Parameters | Sparsity (%) | Top-1 Acc (%) | Model Links |
| ------------ | :--------: | :----------: | :-----------: | :---------: |
| Resnet-50        | 25.50M  | 0.00        | 77.04         | [Base Model](https://drive.google.com/file/d/1I7dxZD87-Ftav-BvIxqCWCWGWqYZFVK2/view?usp=sharing) |
| WideResNet-28-8  | 23.34M  | 0.00        | 96.04         | [Base Model](https://drive.google.com/file/d/1ot3xmR-J4fY5NESeJ503RqSTXu59W467/view?usp=sharing) |

### GP and GP+MT Resnet-50 Pruned Models:

These few models are the checkpoints of pruned Resnet-50 on ImageNet models by GP and GP+MT.

| Pruning Method | Sparsity (%) | Top-1 Acc (%) | Model Links |
| -------------- | :----------: | :-----------: | :---------: |
| GP             | 80           | 76.84         | [Pruned Model](https://drive.google.com/file/d/1bjZdFZiXhfh7fyXS-Mz3GOozAGl0yPDR/view?usp=sharing) |
| GP + 0.05% MT  | 80           | 76.81         | [Pruned Model](https://drive.google.com/file/d/1PkB80RD46vfsuWMxenEbjp5Jq6QXoV3M/view?usp=sharing) |
| GP             | 90           | 75.44         | [Pruned Model](https://drive.google.com/file/d/12V1SHhCxyG6QjrVEP-mT3iB33cLzBWNh/view?usp=sharing) |
| GP + 0.05% MT  | 90           | 75.42         | [Pruned Model](https://drive.google.com/file/d/1mTMHvF_-VNHNbpxFEU5mnfmdTNQoIhck/view?usp=sharing) |
| GP             | 95           | 71.63         | [Pruned Model](https://drive.google.com/file/d/1spUS0U2SgB_Dtc0k6pK7wQ24GUD4EnZt/view?usp=sharing) |
| GP + 0.0075% MT| 95           | 71.23         | [Pruned Model](https://drive.google.com/file/d/18bOtvzAq7sKwraGCWuQfwVweqd0kECS0/view?usp=sharing) |
| GP             | 98           | 62.12         | [Pruned Model](https://drive.google.com/file/d/1K9326WN4xh4x_QoNqLo-T8AlQzBYn8zX/view?usp=sharing) |
| GP + 0.0050% MT| 98           | 61.01         | [Pruned Model](https://drive.google.com/file/d/1kOaR07Rgw11jkhr4JZdn5shqVOiG3GT-/view?usp=sharing) |
