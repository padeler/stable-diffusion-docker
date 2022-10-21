FROM tensorflow/tensorflow:2.10.0-gpu

RUN apt update
RUN apt install -y git wget

RUN pip3 install ipykernel

RUN pip3 install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu116
RUN git clone https://github.com/facebookresearch/xformers.git 
RUN cd xformers && git submodule update --init --recursive && pip install -r requirements.txt && pip install -e . 

# RUN pip install diffusers pillow torch transformers \
#   --extra-index-url https://download.pytorch.org/whl/cu116

RUN pip install -qq git+https://github.com/ShivamShrirao/diffusers
RUN pip install -q -U --pre triton
RUN pip install -q accelerate==0.12.0 transformers ftfy bitsandbytes gradio

RUN pip install opencv-python


RUN useradd -m huggingface -s /bin/bash

WORKDIR /home/huggingface

USER huggingface

RUN mkdir -p /home/huggingface/.cache/huggingface \

COPY docker-entrypoint.py /usr/local/bin

# COPY token.txt /home/huggingface
# ENTRYPOINT [ "docker-entrypoint.py" ]
