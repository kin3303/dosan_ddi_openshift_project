# TEST 환경 설치

- Tested with 24GB memory, 8 cores,  Ubuntu 16.04 LTS  

## Step 1. 초기화

```console
  $ sudo su 
  $ sysctl -w vm.max_map_count=262144
  $ sysctl -w fs.file-max=65536
  $ ulimit -n 65536
  $ ulimit -u 4096
  $ git clone https://github.com/kin3303/DDI_OPENSHIFT.git
  $ cd DDI_OPENSHIFT
  $ git checkout testEnv
  $ chmod +x install.sh
  $ ./install.sh
```

## Step 2. Jenkins 이미지 빌드 및 저장 (Option)

- Docker on Docker 되도록 Jenkins 이미지 빌드 후 저장
- 수행후 Docker Compose 파일의 Jenkins 이미지 이름수정 필요
- SCM 에 있는 Dockerfile 기준 1회만 수행
- Dockierfile 에 추가로 작업이 필요 없는 경우 구어놓은 kin3303/jenkins-docker:latest 사용해도 됨

```console
  $ docker login
  $ docker build -t kin3303/jenkins-docker:latest .
  $ docker push kin3303/jenkins-docker:latest 
```

## Step 3. 테스트 환경 구성

```console
  $ chmod +x start.sh
  $ ./start.sh
```

## Step 4. Potainer 활성화

- Portainer 는 5분 내에 admin 계정을 생성해야 사용 가능하다. 

```
  Portainer - http://your-ip-address:9000
```

## Step 5. 결과 확인

```
  Portainer - http://your-ip-address:9000
  Jenkins — http://your-ip-address:8080
  SonarQube — http://your-ip-address:9000
  Nexus — http://your-ip-address:8081
```
