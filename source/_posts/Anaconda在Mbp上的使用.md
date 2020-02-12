---
title: Anaconda在Mbp上的使用
date: 2020-02-12 14:35:43
tags: 
- Python
- Anaconda
categories: Learning
---

# Anaconda在Mbp上的使用

## 安装

从官网上下载安装包进行安装

## 设置

激活Anaconda的设置

```bash
source ~/.bash_profile
```

## 建立虚拟环境

```bash
conda create -n <the env environment name you want> python=3.7
```

激活虚拟环境

```bash
conda activate <the env name>
```

解除虚拟环境

```bash
conda deactivate <the env name>
```

显示Anaconda所有虚拟环境

```bash
conda info --envs
```

删除Conda虚拟环境 

```bash
conda remove -n <the env name> --all
```

使用文件直接配置虚拟环境的模块包

```yml
name: <the env name>
dependencies:
- python=3.7
- pytest
- keras
- tqdm
- Pillow
- pip:
  - tensorflow
```

```bash
conda env create -f env_config.yml
```

