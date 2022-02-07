## Neural Attention Memory

### Requirements

#### 1. Software requirement

- Python >3.6
- Numpy >1.18
- PyTorch >1.4
- CUDA version: 10.2
- cuDNN: 7 
- NVIDIA-Docker: 2.2.2 (optional)

Using NVIDIA-Docker is not mandatory, but we strongly recommend using NVIDIA-Docker pytorch version download from https://ngc.nvidia.com/catalog/containers/nvidia:pytorch

### Installation

-----

Please clone the program into your local work environment using the command provided below. 

```{bash}
git clone https://github.com/msharmaibert2/ibert.git
```

After cloning the program, you should be able to find a folder name called  `ibert` where I-BERT is located.



### Running I-BERT

-----

I-BERT can be simply run from Bash. Below is the most core command line to run I-BERT. 

```bash
python3 AutoEncode.py --net ibert
```


### Options

-----

Our program supports multiple command-line options to provide a better user experience. The below table shows major options that can be simply appended when running the program.

| Options      | Default | Description                                                  |
| ------------ | ------- | ------------------------------------------------------------ |
| --net        | tf      | Model for your task <br>ibert: I-BERT <br>xlnet: XLNet<br>lstm: LSTM seq2seq <br>tf: BERT <br>ibertpos: I-BERT with positional encoding <br>ibert2: I-BERT2 |
| --seq_type   | fib     | task for prediction <br>fib: addition task (NSP Dataset)<br>copy: copy task (NSP Dataset)<br>palin: reverse task (NSP Dataset)<br>ptbc: Penn Tree Bank Character<br>ptbw: Penn Tree Bank Word |
| --digits     | 12      | Max number of training digits <br>(Only supports for algorithmic tests) |
| --batch_size | 32      | Number of epochs                                             |
| --epochs     | 50      | Number of epochs                                             |
| --lr         | 3e-5    | Learning rate                                                |
| --log        | false   | Log training/validation results                              |
| --exp        | 0       | Assign log file identifier when --log is true                |

For example, if we want to run a `Penn Tree Bank Word` dataset with 100 epochs with I-BERT, we can try the following: 

```bash
python3 AutoEncode.py --net ibert --seq_type ptbw --epochs 100
```



### Sample result

-----

Just as in paper, we provide multiple kinds of metrics including training sequence accuracy, training/validation accuracy, and perplexity. Below shows an example output at epoch 50 after executing `python3 AutoEncode.py --net ibert`.



### Result Analysis

-----

If you choose to log the experiment results, they will be saved in the directory `/log/`. The name of the log file follows the format below. 

```
1 2020-05-23 04/25/16 fib ibert.log
```

- 1 here represents the identifier number of each experiment produced by `--exp <N>  ` where `<N>` is an integer
- 2020-05-23 refers to `year-month-date`
- 04/25/16 shows the `hour/min/sec` when the program is executed for the first time. 
- `fib` is the dataset used for the experiment produced by `--seq_type <dataset> ` where `<dataset>` can be among `fib, copy, palin, ptbc, ptbw` 
- `ibert` is the model used for the experiment produced by `--net <model>` where `<model>` can be among `ibert, xlnet, lstm, tf, ibertpos, ibert2`.

### TODO

- Add test dataset (2 digits)
- Add model save/load
- Try LSAM on listops
- Long Range Arena add AM
- Refactoring
