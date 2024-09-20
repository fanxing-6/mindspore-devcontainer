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

# Create a new conda environment with Python 3.9
RUN conda create -n mindspore39 python=3.9 -y

# Activate the new environment and install MindSpore
SHELL ["conda", "run", "-n", "mindspore39", "/bin/bash", "-c"]


# Set the default command to bash, activating the mindspore39 environment
CMD ["conda", "run", "--no-capture-output", "-n", "mindspore39", "/bin/bash"]