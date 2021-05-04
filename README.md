# KHU 드롭박스 프로젝트

## How to deploy

ElasticBeanstalk을 이용하면 편리하게 배포를 자동화할 수 있지만 AWS Educate를 이용하면서는 IAM User key 발급이 지원되지 않고,
교수님께서 설정하신 AWS Educate Classroom 설정으로는 ElasticBeanstalk을 사용할 수 없었습니다. 따라서 직접 EC2에 SSH 접속을
해서 컨테이너를 지운 뒤 새로운 컨테이너를 띄우는 방식으로 배포합니다.

필요한 항목은 다음과 같고 모두 @umi0410(박진수 팀원)에게서 제공받을 수 있습니다.

1. EC2 접속을 위한 ssh pem key 
2. 원활한 ssh 명령어 수행을 위한 ssh config
3. Github package의 container registry에 로그인하기 위한 Github token

```shell
$ docker login ghcr.io -u umi0410
```

전달 받은 .pem key과 config를 .ssh에 저장합니다. 이후 아래 커맨드를 통해 container registry에 인증합니다.

```shell
$ ./script/deploy.sh
```

앞서 설명한 설정이 완료되면 간단히 위의 커맨드로 EC2 서버에 현재 작업물을 배포할 수 있습니다.