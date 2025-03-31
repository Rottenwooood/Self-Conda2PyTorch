# 使用官方的基础镜像
FROM mcr.microsoft.com/devcontainers/base:ubuntu

# 安装依赖工具
RUN apt-get update && apt-get install -y \
    wget \
    bzip2 \
    && rm -rf /var/lib/apt/lists/*

# 下载并安装 Miniconda
RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /tmp/miniconda.sh \
    && bash /tmp/miniconda.sh -b -p /opt/conda \
    && rm /tmp/miniconda.sh

# 将 Conda 添加到 PATH
ENV PATH="/opt/conda/bin:$PATH"

# 更新 Conda 到最新版本
RUN conda update -n base -c defaults conda

# 设置默认的 Python 版本（可选）
RUN conda create -n base python=3.9 -y

# 清理缓存以减小镜像大小
RUN conda clean -a -y