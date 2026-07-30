# Terminal_Docker Mission

---

# 1. 프로젝트 개요

## 목표

#### 1. Ubuntu + Git + Docker를 터미널 조작 방법, Git/GitHub, Docker에 대한 실습
#### 2. 단순한 실습에 그치지 않고 구조를 이해하고 스스로 사용하기


---

# 2. 실행 환경

|항목|내용|
|---|---|
|Host OS|Window|
|Linux 환경|WSL2 Ubuntu 24.04.4 LTS|
|Shell|Bash|
|Terminal|Windows Termianl|
|Docker|Docker Desktop 29.6.2|
|Git|2.43.0|

---

# 3. 수행 체크리스트

|항목|완료|
|---|:---:|
|터미널 조작 명령어 |✅|
|권한 실습 |✅|
|Docker 설치 및 기본 점검|✅|
|Docker 기본 운영 명령 수행|✅|
|Docker 컨테이너 실행|✅|
|Dockerfile 작성|✅|
|웹 서버 실행|✅|
|포트 매핑|✅|
|Bind Mount|✅|
|Volume|✅|
|Git/GitHub 설정 및 연동|✅|


----


# 4. 터미널 조작 로그
### 1. 현재 위치 확인 (pwd)
![](./screenshot/terminal-images/pwd.png)
### 2. 목록 확인(숨긴 파일 포함) (ls)
![](./screenshot/terminal-images/ls.png)
### 3. 이동 (cd)
![](./screenshot/terminal-images/cd.png)
### 4. 생성 (mkdir)
![](./screenshot/terminal-images/mkdir.png)
### 5. 복사 (cp)
![](./screenshot/terminal-images/filecopy.png)
![](./screenshot/terminal-images/folder-copy-1.png)
![](./screenshot/terminal-images/folder-copy-2.png)
### 6. 이동/이름변경 (mv)
파일 이름 변경
![](./screenshot/terminal-images/mv_change_name.png)
폴더 이름 변경
![](./screenshot/terminal-images/mv_change_folder.png)
이동
![](./screenshot/terminal-images/mv-move-1.png)
![](./screenshot/terminal-images/mv-move-2.png)
이동 + 이름 변경
![](./screenshot/terminal-images/mv-move-change.png)
### 7. 삭제 (rm)
파일 삭제
![](./screenshot/terminal-images/rm-1.png)
폴더 삭제
![](./screenshot/terminal-images/rm-r.png)
### 8. 파일 내용 확인 (cat, less, more, head, tail)
![](./screenshot/terminal-images/cat.png)
### 9. 빈 파일 생성 (touch)
![](./screenshot/terminal-images/touch.png)
### 10. etc

---

# 5. 권한 실습 및 증거 기록
### 1. 권한 확인 명령어 (ls -l)
![](./screenshot/terminal-images/ls-l.png)
### 2. 파일 권한 변경 및 확인 (chmod)
![](./screenshot/terminal-images/chmod_file.png)
### 3. 폴더 권한 변경 및 확인 (chmod)
![](./screenshot/terminal-images/chmod_folder.png)


---


# 6. Docker 설치 및 기본 점검
### 1. Docker 버전 확인 결과 (docker --version)
![](./screenshot/docker-images/docker_version.png)
### 2. Docker 데몬 동작 여부 (docker --info)
![](./screenshot/docker-images/docker_info.png)
![](./screenshot/docker-images/docker_info_info.png)

--- 

# 7. Docker 기본 운영 명령 수행

### 1. 이미지 : 다운로드/목록 확인 (full, images)
다운로드
![](./screenshot/docker-images/docker-pull.png)
이미지 목록 확인
![](./screenshot/docker-images/docker-images.png)

### 2. 컨테이너 : 생성/실행/중지/목록 확인
컨테이너 생성
![](./screenshot/docker-images/docker-create.png)
컨테이너 실행
![](./screenshot/docker-images/docker-start.png)
컨테이너 생성 + 실행
![](./screenshot/docker-images/docker-run.png)
컨테이너 중지
![](./screenshot/docker-images/docker-ps-stop.png)
컨테이너 목록 확인
![](./screenshot/docker-images/docker-container-list.png)


### 3. 운영 : 로그 확인, 리소스 확인
로그 확인
![](./screenshot/docker-images/docker-logs.png)
리소스 확인
![](./screenshot/docker-images/docker-resource.png)

---


# 8. 컨테이너 실행 실습
### 1. hello-world 실행 성공을 기록
![](./screenshot/docker-images/docker-hello-world.png)

### 2. ubuntu 컨테이너 실행, 간단 명령
![](./screenshot/docker-images/docker-run-ubuntu.png)

### 3. 컨테이너 종료/유지(attach, exec)
컨테이너 생성 및 확인
![](./screenshot/docker-images/docker-container-ae.png)
attach 확인
![](./screenshot/docker-images/docker-attach.png)
exec 확인
![](./screenshot/docker-images/docker-exec.png)



---


# 9. 기존 Dockerfile 기반 커스텀 이미지 제작

사전 작업
![](./screenshot/docker-images/docker-custom-1.png)

Dockerfile에 기재
```
FROM ubuntu:24.04

# 패키지 설치
RUN apt update && \
    apt install -y vim git curl && \
    apt clean

# 사용자 생성
RUN useradd -m student

# 환경변수
ENV MY_NAME=Hong

# 작업 폴더
WORKDIR /workspace

CMD ["/bin/bash"]
```

빌드
![](./screenshot/docker-images/docker-custom-2.png)

컨테이너 실행
![](./screenshot/docker-images/docker-custom-3.png)

커스텀 포인트
![](./screenshot/docker-images/docker-custom-git.png)

![](./screenshot/docker-images/docker-custom-vim.png)

---


# 10. Dockerfile 기반 웹 서버 컨테이너
구조
![](./screenshot/docker-images/docker-web-server-1.png)

index.html
![](./screenshot/docker-images/docker-web-server-2.png)

dockerfile
![](./screenshot/docker-images/docker-web-server-3.png)

build
![](./screenshot/docker-images/docker-web-server-4.png)
![](./screenshot/docker-images/docker-web-server-5.png)

컨테이너 만들고 실행 + 포트 매핑
![](./screenshot/docker-images/docker-web-server-6.png)

최종 결과
![](./screenshot/docker-images/docker-web-server-7.png)

---


# 11. 포트 매핑 및 접속 증거
포트 매핑 명령어
![](./screenshot/docker-images/docker-port-1.png)

브라우저 접속 화면
![](./screenshot/docker-images/docker-port-2.png)

curl 응답 
![](./screenshot/docker-images/docker-curl-1.png)

![](./screenshot/docker-images/docker-curl-2.png)


---


# 12. Docker 볼륨 영속성 검증
볼륨 생성
![](./screenshot/docker-images/docker-volume-1.png)

볼륨 연결
![](./screenshot/docker-images/docker-volume-2.png)

볼륨에 데이터 추가
![](./screenshot/docker-images/docker-volume-3.png)

연결했던 컨테이너 삭제
![](./screenshot/docker-images/docker-volume-4.png)

다른 컨테이너 연결하고 데이터 살아있는지 확인
![](./screenshot/docker-images/docker-volume-5.png)


---


# 13. 바인드 마운트
![](./screenshot/docker-images/docker-bind-mount-1.png)
![](./screenshot/docker-images/docker-bind-mount-2.png)
![](./screenshot/docker-images/docker-bind-mount-3.png)
![](./screenshot/docker-images/docker-bind-mount-4.png)
![](./screenshot/docker-images/docker-bind-mount-5.png)
![](./screenshot/docker-images/docker-bind-mount-6.png)



---


# 12. Git 설정 및 GitHub 연동


---


# 13. 보안 및 개인정보 보호
