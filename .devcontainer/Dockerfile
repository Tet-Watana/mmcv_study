# Use the NVIDIA CUDA image as the base
FROM nvidia/cuda:12.1.0-cudnn8-devel-ubuntu20.04

# Set the working directory in the container
WORKDIR /workdir

# Install PyTorch and MMCV
# Replace the following command with the specific command you use to install PyTorch and MMCV
RUN apt update && apt install -y apt-utils sudo build-essential python3-pip git
RUN DEBIAN_FRONTEND=noninteractive TZ=Asia/Tokyo apt-get -y install tzdata
RUN apt install -y libgl1-mesa-glx libglib2.0-0
RUN pip install --upgrade pip
RUN pip3 install pip-tools
COPY ./build/requirements.in /workdir/data/build/requirements.in
RUN pip-compile /workdir/data/build/requirements.in
RUN pip3 install -r ./data/build/requirements.txt
RUN mim install mmcv
# RUN python3 ./data/repo/mmcv/.dev_scripts/check_installation.py 


# Command to run when starting the container
CMD ["/bin/bash"]
