## Docker 설치 (필수)

- Tested with 24GB memory, 8 cores,  Ubuntu 16.04 LTS  

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


## Jenkins 설치 (옵션)

### Step 1. Jenkins 이미지 빌드 및 저장 (필요시만)

- Docker on Docker 되도록 Jenkins 이미지 빌드 후 저장
- 수행후 Docker Compose 파일의 Jenkins 이미지 이름수정 필요
- SCM 에 있는 Dockerfile 기준 1회만 수행
- Dockierfile 에 추가로 작업이 필요 없는 경우 구어놓은 kin3303/jenkins-docker:latest 사용해도 됨

```console
  $ docker login
  $ docker build -t kin3303/jenkins-docker:latest .
  $ docker push kin3303/jenkins-docker:latest 
```

###  Step 2. Jenkins 설치

```console
  $ chmod +x start-jenkins.sh
  $ ./start-jenkins.sh
```

### Step 3. Potainer 설정

- Portainer 는 5분 내에 admin 계정을 생성해야 사용 가능하다. 

```
  Portainer - http://your-ip-address:9000
```
