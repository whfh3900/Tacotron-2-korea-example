# Tacotron2-korea-example
## 2018년 구글에서 새로운 TTS 모델인 Tacotron 2를 발표하였다. 구글이 자신들의 블로그에서 주장하기를 거의 사람이 직접 내는 음성과 비슷한 퀄리티의 음성을 생성할 수 있는 모델이라고 홍보하고 있는데 실제로 Tacotron 2가 생성한 음성 샘플을 들어보면 사람의 목소리인지 구분하기 힘들 정도다.
- 본 소스코드는 포트폴리오 용으로 작성한 것이고, 실제 코드는 https://github.com/Rayhane-mamah/Tacotron-2 기반으로 작성하였다. 
2019년 2월에 Tacotron에 관심가지게 되어 Tacotron2 code를 분석하다가 개인 사정에 의해 잠시 분석을 중단하였는데 현재 구글링을 해보니 Tacotron3가 나온것 같아서 나중에 꼭 한번 시도해 봐야겠다. 현 버젼의 Tacotron의 개인적인 단점은 합성하는데 시간이 걸린다는 점이다. 실시간 음성합성 기술로는 적합하지 않다. Taotron3는 이러한 문제를 해결한 것일까?(https://github.com/StevenLOL/tacotron-3.git)

# Install
falcon==1.2.0
inflect==0.2.5
audioread==2.1.5
librosa==0.5.1
matplotlib==2.0.2
numpy==1.14.0
scipy==1.0.0
tqdm==4.11.2
Unidecode==0.4.20
pyaudio==0.2.11
sounddevice==0.3.10
lws
keras
nltk==3.3
jamo==0.4.1

- 해당 명령어를 통해 필요한 패키지를 설치 할 수 있다.
`pip install -r requirments.txt

# Datasets
이 곳에서 음성데이터셋뿐만 아니라 딥러닝을 이용한 음성합성 관련 자료들이 나와있다.
https://github.com/lifefeel/SpeechSynthesis

# Process
## 1. preprocess 실행
`python preprocess_audio.py
`python preprocess.py
## 2. Training
`python train.py
실행하기 전에 hparams.py에서 하이퍼파라미터를 설정하거나 argument를 설정하여 실행하는 것을 권장한다. 이것으로 Tacotron과 Wavenet 훈련 gpu 사용 갯수 및 Tactron 또는 Wavenet만 실행 시킬 수도 있다.
또한 만약 Tactron2 모델을 학습할 때 Tacotron 학습이 끝난 후 Wavenet으로 넘어가기 전에 Tacotron의 합성결과를 tacotron_output에서 확인할 수 있다.
#### example
`python train.py --tacotron_num_gpus = 1 --wavenet_num_gpus = 2
## 3. Synthesize
'python synthesize.py
웨이브넷까지 최종합성 완료가 되면 wavenet_output폴더가 생성되어 안에 합성결과가 들어가 있다.
