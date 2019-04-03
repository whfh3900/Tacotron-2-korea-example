ARG IMAGE_NAME
FROM ${IMAGE_NAME}:9.0-devel-ubuntu16.04
LABEL maintainer "NVIDIA CORPORATION <cudatools@nvidia.com>"

ENV CUDNN_VERSION 7.4.2.24
LABEL com.nvidia.cudnn.version="${CUDNN_VERSION}"

RUN apt-get update && apt-get install -y --no-install-recommends \
		libcudnn7=$CUDNN_VERSION-1+cuda9.0 \
		libcudnn7-dev=$CUDNN_VERSION-1+cuda9.0 && \
		apt-mark hold libcudnn7 && \
		rm -rf /var/lib/apt/lists/*

FROM continuumio/anaconda3:latest
FROM tensorflow/tensorflow:1.10.0-devel-gpu-py3

RUN apt-get update
RUN apt-get install -y libasound-dev portaudio19-dev libportaudio2 libportaudiocpp0 ffmpeg libav-tools wget git vim

#RUN wget http://data.keithito.com/data/speech/LJSpeech-1.1.tar.bz2
#RUN tar -jxvf LJSpeech-1.1.tar.bz2

RUN git clone https://github.com/Yeongtae/Tacotron-2-kor.git

WORKDIR Tacotron-2-kor
#RUN ln -s ../LJSpeech-1.1 .
RUN pip install -r requirements.txt
RUN pip install tensorflow-gpu==1.10
