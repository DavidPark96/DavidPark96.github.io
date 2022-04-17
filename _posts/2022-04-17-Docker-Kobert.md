---
title: Docker kobert 설치

layout: single

categories:
  - aib
tags:
  - [docker, kobert, pytorch]
toc: true
toc_sticky: true
---

# Docker에 Kobert 설치하기

## pytorch image pull  
docker hub 공식 pytorch에 cuda tool kit도 깔려있어서 gpu 사용 가능

https://greeksharifa.github.io/references/2021/06/21/Docker/  
https://hub.docker.com/r/pytorch/pytorch/tags?page=1&name=10.2-cudnn


```python
#최신버전
docker pull pytorch/pytorch:latest
```


```python
#pytorch 공식 지원 cuda 구버전
docker pull pytorch/pytorch:1.9.0-cuda10.2-cudnn7-runtime
```


```python
docker run -it --gpus all --name prj_gorio pytorch/pytorch:1.6.0-cuda10.1-cudnn7-devel /bin/bash
```

-it	Iterative Terminal. Container 종료 없이 탈출 가능.  
–name, -n	Container의 이름을 지정한다. 안 쓰면 nice_spence 같은 임의의 이름으로 생성된다.  
–volume, -v	Container와 공유할 디렉토리를 지정한다. -v <외부 Dir>:<Container Dir> 형식으로 쓴다. 파일 생성/수정/삭제가 동기화된다.  
–gpus all	Container 내부에서 GPU를 쓸 수 있도록 한다. nvidia toolkit이 설치되어 있어야 한다.  
/bin/bash	Container 생성 시 시작할 프로세스이다. bash의 설치 위치에 따라 적당히 변경하면 된다.  

## unbuntu에 깃 설치하기  
https://yangeok.github.io/devops/2019/01/19/git-in-docker-container.html


```python
apt-get update && apt-get install -y git
```

## kobert 설치시 gcc오류  
https://serverfault.com/questions/528884/unable-to-execute-gcc-no-such-file-or-directory


```python
apt-get install gcc
```

## kobert 설치  
https://github.com/SKTBrain/KoBERT


```python
pip install git+https://git@github.com/SKTBrain/KoBERT.git@master
```

## vscode에서 docker작업하기
https://89douner.tistory.com/123


```python
'ctrl+shift+p'를 클릭하시고 'remote-containers: attach to Running Container...'을 입력하시고 클릭해주세요. 
```

## Dockerfile로 이미지 빌드하고 컨테이너 띄워보기
https://nicewoong.github.io/development/2018/03/06/docker-commit-container/


```python
docker commit CONTAINER IMAGE_NAME
```

## pip list로 freeze하기
https://stackoverflow.com/questions/62863020/pip-freeze-generating-file-on-conda-environment

```python
pip list --format=freeze > requirements.txt
```