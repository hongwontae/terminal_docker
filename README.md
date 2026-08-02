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
### 4. 파일 권한 변경 + 이진수 (421)
![](./screenshot/terminal-images/chmod-421.png)


---


# 6. Docker 설치 및 기본 점검
### 1. Docker 버전 확인 결과 (docker --version)
![](./screenshot/docker-images/docker_version.png)
### 2. Docker 데몬 동작 여부 (docker info)
데몬 = 엔진 / Container, images, Server Version
![](./screenshot/docker-images/docker_info.png)
![](./screenshot/docker-images/docker_info_info.png)

--- 

# 7. Docker 기본 운영 명령 수행

### 1. 이미지 : 다운로드/목록 확인 (full, images)
다운로드
![](./screenshot/docker-images/docker-pull.png)
이미지 목록 확인
이미지 -> 컨테이너를 만들기 위한 읽기 전용 설계도입니다.
![](./screenshot/docker-images/docker-images.png)

### 2. 컨테이너 : 생성/실행/중지/목록 확인
컨테이너 생성
=> 컨테이너는 Image 기반으로 만들어진 실행환경입니다. -> 프로세스
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
apt -> 우분투 계열 리눅스 패키지 관리 도구

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
-t는 빌드로 생성할 이미지에 이름을 붙이는 것
.은 경로
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
### 1. git 사용자 정보/기본 브랜치 설정을 완료하고 git confg --list 결과
![](./screenshot/git-images/git-config-1.png)


### 2. GitHub 로그인 및 저장소 연동 + SSH 연동
![](./screenshot/git-images/github-ssh-1.png)

SSH
![](./screenshot/git-images/github.ssh-2.png)

![](./screenshot/git-images/github-ssh-3.png)

![](./screenshot/git-images/github-ssh-4.png)

연동
![](./screenshot/git-images/git-github-1.png)
![](./screenshot/git-images/git-github-2.png)
![](./screenshot/git-images/git-github-3.png)
![](./screenshot/git-images/git-github-4.png)


---


# 13. 보안 및 개인정보 보호

### 1. Git - GitHub 연동할 때 SSH를 사용
공개키 암호화 전략

내 컴퓨터에 개인키가 존재하고 GitHub에 공개키를 저장합니다. 그 후 GitHub이 

인증을 하라고 내 컴퓨터 요청을 보냅니다. 그리고 

컴퓨터에서 개인키로 서명을 만들고 GitHub에서 등록된

공개키로 서명이 맞는지 확인합니다. 즉, 여기서 보안을 

위해서는 개인키는 철저히 감춰야 합니다. -> 12에서는 공개키는 보이지만 개인키는 보이지 않습니다.


### 2. gitignore
프로그램을 만들거나 공부하면서 API_Key 같은 정보가 파일 상에 존재할 때가 있습니다.

이 떄 github에 그대로 올리면 악의적인 공격을 받을 수 있습니다.

git -> github으로 commit할 떄 .gitignore을 사용하면 원치 않는 파일을 commit 하지 않아 원하는 파일만 올릴 수 있습니다.

# 14. 트러블 슈팅
### 1-1. 문제
1-1. rm 터미널 명령어로 폴더 삭제가 안되는 문제 발생

### 1-2. 원인 가설
1-2. rm 명령어를 통해 파일은 잘 삭제되었음. 그러면 폴더를 삭제하는 옵션이 필요한게 아닌지 가설

### 1-3. 확인
1-3. ChatGPT를 통해 폴더를 삭제하는 명령어 알려달라고 부탁

### 1-4. 해결/대안
1-4. 폴더를 삭제할 떄는 -r를 통해 재귀적으로 삭제하거나 -rf를 통해 재귀적 + 강제적으로 삭제할 수 있다는 것을 깨달음

![](./screenshot/terminal-images/rm-troble-1.png)

--- 


### 2-1. 문제
2-1. 컨테이너 목록이 제대로 식별되지 않음

### 2-2. 원인 가설
2-2. 컨테이너를 분명히 만들었는데 보이지 않아서 다른 옵션을 줘야 보일것이라고 판단

### 2-3. 확인
2-3. ChatGPT에게 컨테이너를 식별할 수 있는 방법에 대해서 부탁

### 2-4. 해결/대안
2-4. docker ps는 실행중인 컨테이너만 보이고 docker ps -a를 사용해야 실행, 실행 x 모두 보인다고 알려줌. 이를 통해 docker ps -a 존재대해 공부

![](./screenshot/docker-images/docker-troble-1.png)
