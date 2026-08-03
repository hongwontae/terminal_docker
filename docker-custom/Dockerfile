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