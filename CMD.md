##### 실습 환경 초기화 

```bash
docker container rm -f $(docker container ls -aq)  # 컨테이너 삭제 
docker image rm -f $(docker image ls -f reference='diamol/*' -q) # 디스크 용량 모드 회수 
```

<br>



##### 컨테이너 실행 

```bash
docker container run --detach --publish 8088:80 diamol/ch02-hello-diamol-web
```

* --detach : 컨테이너를 백그라운드에서 실행하며 컨테이너 ID 출력 

  ​	=> 사용자 인터페이스 없이 배치잡처럼 동작  

* --publsh : 컨테이너 포트를 호스트 컴퓨터에 공개 

<br>

```bash
docker container run --env TARGET = google.com 
```

<br> 



##### 컨테이너 내부 터미널 접속 (터미널 세션)

```bash
docker container run --interactive --tty diamol/base 
```

<br>

##### 자주쓰는 명령어 

```bash
docker container ls 
```



##### 도커 허브 

```bash
docker image pull diamol/ch03-web-ping
```

