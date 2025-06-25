---
title: "如何用 MacOS 下使用 GPT-SoVITS"
date: 2024-02-02T20:16:34+08:00
draft: false
---
<!-- # 如何用 MacOS 下使用 GPT-SoVITS -->
# 前言
第一次配置环境时，用了一个钟，踩了不少坑。现整理出来，方便大家快速在自己的 Mac 上启动 GPT-SoVITS。
# 环境和前置准备
## 我的硬件环境：
用的是 MacBook Air M2 内存 16G，系统版本是 macOS 14.3。
有统一内存架构，所以不需要额外的显卡。用来上手 GPT-SoVITS 是绰绰有余的。

## 软件环境：
- 已通过运行xcode-select --install安装 Xcode command-line tools
- 安装好 Miniconda 
- 如果你会给 Conda 换源，那么也不需要魔法上网
- 安装好了 git 、ffmpeg 、huggingface-cli

### 安装 ffmpeg
```bash
# 安装 ffmpeg
brew install ffmpeg
# 查看版本
ffmpeg -version
```

# 拉取代码、创建环境、安装依赖
```bash
# 拉取项目代码
git clone --depth=1 https://github.com/RVC-Boss/GPT-SoVITS
cd GPT-SoVITS

# 安装好 Miniconda 之后，先创建一个虚拟环境：
conda create -n GPTSoVits python=3.9
conda activate GPTSoVits

# 安装依赖：
pip3 install -r requirements.txt
pip3 uninstall torch torchaudio
pip3 install --pre torch torchaudio --index-url https://download.pytorch.org/whl/nightly/cpu

# (可选)如果网络环境不好，可以考虑换源(比如清华源)：
pip3 install -i https://pypi.tuna.tsinghua.edu.cn/simple -r requirements.txt
pip3 uninstall torch torchaudio
pip3 install --pre torch torchaudio --index-url https://download.pytorch.org/whl/nightly/cpu
```

# 下载模型
```bash
# 安装 huggingface-cli 用于和 huggingface hub 交互
pip3 install huggingface_hub
# 登录 huggingface-cli
hugging face-cli login

# 下载模型, 由于模型文件较大，可能需要一段时间
# --local-dir-use-symlinks False 用于解决 macOS alias 文件的问题
# 会下载到 GPT_SoVITS/pretrained_models 文件夹下
huggingface-cli download --resume-download lj1995/GPT-SoVITS --local-dir GPT_SoVITS/pretrained_models --local-dir-use-symlinks False
```

# 运行
```bash
python webui.py
```

本文最早是发布在 [GPT SoVITS 语雀文档中](https://www.yuque.com/baicaigongchang1145haoyuangong/ib3g1e/znoph9dtetg437xb) 上，现在已经过多轮升级，最新版请访问最新版本。