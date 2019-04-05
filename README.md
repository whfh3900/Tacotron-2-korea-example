# Tacotron-2-korea-example

1. docker를 이용해서 실행하는 것을 권장한다.
2. Tacotron-2-korea-example/docker/Dockerfile 만 다운받고 아래명령으로 docker image를 생성한다.
user@user-B360M-DS3H:~/tacotron2-kor-docker$ docker build --build-arg IMAGE_NAME=nvidia/cuda -t 이미지이름 Dockerfile경로

3. 이미지생성 후 컨테이너 생성
user@user-B360M-DS3H:~/tacotron2-kor-docker$ nvidia-docker run -it -p 포트번호(ex)6006:6006)--name 컨테이너이름 이미지이름 /bin/bash

4. dataset 받기
- 일단 exit명령어로 다시 home으로 돌아온후 kss dataset을 다운받는다(https://www.kaggle.com/bryanpark/korean-single-speaker-speech-dataset)

5. 아래명령어를 통해 데이터셋을 docker로 보내기
user@user-B360M-DS3H:~/tacotron2-kor-docker$ docker cp 데이터셋이름 컨테이너이름:보낼경로

6. 다시 docker실행
user@user-B360M-DS3H:~/tacotron2-kor-docker$ docker start 컨테이너이름
user@user-B360M-DS3H:~/tacotron2-kor-docker$ docker exec -i -t 컨테이너이름 /bin/bash

7. 
