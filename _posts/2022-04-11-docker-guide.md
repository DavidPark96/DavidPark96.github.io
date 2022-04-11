---
title: Docker 가이드

layout: single

categories:
  - aib
tags:
  - [docker]
toc: true
toc_sticky: true
---
# 1. 레지스트리에서 이미지 혹은 레포지토리를 가져오기


```python
docker image pull [registry_account]/[repository_name]:[tag]
```

# 2. 이미지 리스트


```python
docker image ls
```

# 3. 이미지 -> 컨테이너

[image] = [registry_account]/[repository_name]:[tag]


```python
docker container run --name [container_name] [IMAGE] [COMMAND] [ARG]
```

## 3-1. 일회성 실행 

--rm 옵션 : 컨테이너가 종료될 때 컨테이너와 관련된 리소스를 모두 제거합니다.


```python
docker container run --name [container_name] --rm [IMAGE] [COMMAND] [ARG]
```

## 3-2. 명령 옵션


```python
docker container run -it --rm [IMAGE]
```

# 4. 컨테이너 리스트 출력

-a 옵션은 실행중이지 않은 컨테이너 전체 조회


```python
docker container ps -a
```

# 5. 컨테이너를 삭제하는 명령어


```python
docker container rm [container_name]
```

# 6. 이미지 지우기


```python
docker image rm [IMAGE]
```

# 7. httpd

Apache HTTP Server 를 실행할 수 있는 오픈소스 웹 서버 소프트웨어

-p 옵션 : 로컬(호스트)의 포트와 컨테이너의 포트와 연결시킵니다.


```python
docker container run --name [container_name] --rm -p [port]:80 httpd
```

localhost:[port]

# 8. 로컬, 컨테이너 데이터 복사

## 8-1.로컬 -> 컨테이너


```python
docker container cp ./ [container_name]:[container_path]/
```

## 8-2.컨테이너 ->로컬


```python
docker container cp [container_name]:[container_path]/ ./
```

# 9. Docker Container 를 이미지로 만드는 방법


```python
docker container commit [container_name] [image]:[tag]
```

# 10. Docker Image 빌드를 위한 파일인 Dockerfile 로 만드는 방법


```python
docker build --tag [image]:[tag]
```

# 11.ENV


```python
docker run --name [container_name] -it -d --env [ENV]=[param] [image]:[tag]
```

# 12. 배쉬열기


```python
docker exec -it [container_name] bash
```
