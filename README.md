# Tacotron-2-korea-example

1. docker를 이용해서 실행하는 것을 권장한다.
2. Tacotron-2-korea-example/docker/Dockerfile 만 다운받고 아래명령으로 docker image를 생성한다.
- user@user-B360M-DS3H:~/tacotron2-kor-docker$ docker build --build-arg IMAGE_NAME=nvidia/cuda -t 이미지이름 Dockerfile경로

3. 이미지생성 후 컨테이너 생성
- user@user-B360M-DS3H:~/tacotron2-kor-docker$ nvidia-docker run -it -p 포트번호(ex)6006:6006)--name 컨테이너이름 이미지이름 /bin/bash

4. dataset 받기
- 일단 exit명령어로 다시 home으로 돌아온 후 kss dataset을 다운받고 안에 있는 kss까지 압축을 푼다.(https://www.kaggle.com/bryanpark/korean-single-speaker-speech-dataset)

5. 아래명령어를 통해 데이터셋을 docker로 보내기
- user@user-B360M-DS3H:~/tacotron2-kor-docker$ docker cp 데이터셋이름 컨테이너이름:보낼경로

6. 다시 docker실행
- user@user-B360M-DS3H:~/tacotron2-kor-docker$ docker start 컨테이너이름
- user@user-B360M-DS3H:~/tacotron2-kor-docker$ docker exec -i -t 컨테이너이름 /bin/bash

7. preprocess 실행
- root@918942e88c7a:~/Tacotron-2-korea-example# python preprocess_audio.py
- root@918942e88c7a:~/Tacotron-2-korea-example# python preprocess.py

8. training 실행
- root@918942e88c7a:~/Tacotron-2-korea-example# python train.py
- multi-gpu를 사용하고 싶은 경우 hparams.py를 참조하여 hparams.py의 변수를 바꿔주거나 train.py 실행 명령어를 바꿔준다.

9. tensorborad 실행
- 타코트론을 보고 싶은 경우
- root@918942e88c7a:~/Tacotron-2-korea-example# tensorboard --logdir ./logs-Tacotron-2/tacotron_events --port 포트번호
- 웨이브넷을 보고 싶은 경우
- root@918942e88c7a:~/Tacotron-2-korea-example# tensorboard --logdir ./logs-Tacotron-2/wavenet_events --port 포트번호
- 그 후 파이어폭스를 킨후 https://localhost:포트번호에 접속하면 training 그래프를 볼 수 있다.

10. 음성합성
- root@918942e88c7a:~/Tacotron-2-korea-example# python synthesize.py
- 웨이브넷까지 최종합성 완료가 되면 wavenet_output폴더가 생성되어 안에 합성결과가 들어가 있다.

