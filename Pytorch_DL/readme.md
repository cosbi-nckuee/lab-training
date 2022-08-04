[![Maintenance](https://img.shields.io/badge/Maintained-no-red.svg)](https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
[![Generic badge](https://img.shields.io/badge/Model-passing-green.svg)](https://shields.io/)
[![Generic badge](https://img.shields.io/badge/Plotting-passing-green.svg)](https://shields.io/)
[![Generic badge](https://img.shields.io/badge/dataset-passing-green.svg)](https://shields.io/)

# Pytorch and Deep Learning Intro

Building LeNet-5 in [PyTorch](https://pytorch.org/) with [MNIST dataset](http://yann.lecun.com/exdb/mnist/).
[Jupyter notebook](./resources/mnist_tutorial.ipynb) and
[PPT](./resources/MNIST_TUTORIAL.pdf) are available in `resources/` folder.

## Structure

```text
pytorch_intro/
├── resources
├── submission
├── data
├── main.py
├── model.py
└── utils.py
```

## Requirement

1. pytorch
2. matplotlib
3. torchsummary
4. tqdm

>Install packages by requirements.txt is not recommended,
>You should check your GPU to install the proper version of Pytorch.

```bash
#pip install -r requirements.txt # this may arise package error
```

## RUN

**Clone repo:**

```bash
https://github.com/cosbi-nckuee/lab-training.git
```

**Parameters detail:**

```bash
python main.py -h
```

**Training:**

```bash
python main.py -m train -bs 64 -epo 4 -lr 5e-4
```

**Predict:**

```bash
python main.py -m pred -bs 64
```
