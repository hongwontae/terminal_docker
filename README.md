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

