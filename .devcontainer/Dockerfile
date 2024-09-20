FROM swr.cn-south-1.myhuaweicloud.com/mindspore/mindspore-gpu-cuda11.6:2.2.14
LABEL authors="root"

# Install wget
RUN apt-get update && apt-get install -y wget && rm -rf /var/lib/apt/lists/*

# Download and install Miniconda
RUN mkdir -p /root/miniconda3 \
    && wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /root/miniconda3/miniconda.sh \
    && bash /root/miniconda3/miniconda.sh -b -u -p /root/miniconda3 \
    && rm /root/miniconda3/miniconda.sh

# Initialize conda for bash
RUN /root/miniconda3/bin/conda init bash

# Make sure the conda command is available in subsequent RUN commands
ENV PATH="/root/miniconda3/bin:${PATH}"

# Install MindSpore
RUN pip install https://ms-release.obs.cn-north-4.myhuaweicloud.com/2.2.14/MindSpore/unified/x86_64/mindspore-2.2.14-cp39-cp39-linux_x86_64.whl --trusted-host ms-release.obs.cn-north-4.myhuaweicloud.com -i https://pypi.tuna.tsinghua.edu.cn/simple

# Set the default command to bash
CMD ["/bin/bash"]
