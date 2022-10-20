# 8.2.-DevOps.-CI-CD
## HomeWork

---

### 1. Первое задание
```
Started by user DVakhrameev
Running as SYSTEM
Building in workspace /var/lib/jenkins/workspace/test
The recommended git tool is: NONE
No credentials specified
 > git rev-parse --resolve-git-dir /var/lib/jenkins/workspace/test/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/netology-code/sdvps-materials.git # timeout=10
Fetching upstream changes from https://github.com/netology-code/sdvps-materials.git
 > git --version # timeout=10
 > git --version # 'git version 2.30.2'
 > git fetch --tags --force --progress -- https://github.com/netology-code/sdvps-materials.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/master^{commit} # timeout=10
Checking out Revision da5acf7bcb7f437637adf06fbd03a24dc2c8f13e (refs/remotes/origin/master)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f da5acf7bcb7f437637adf06fbd03a24dc2c8f13e # timeout=10
Commit message: "branch main, add creds for vagrant box"
 > git rev-list --no-walk da5acf7bcb7f437637adf06fbd03a24dc2c8f13e # timeout=10
[test] $ /bin/sh -xe /tmp/jenkins14416538363385454163.sh
+ /usr/local/go/bin/go test .
ok  	github.com/netology-code/sdvps-materials	(cached)
[test] $ /bin/sh -xe /tmp/jenkins2980038423542922225.sh
+ echo /var/lib/jenkins/workspace/test
/var/lib/jenkins/workspace/test
+ ls -nahl
total 40K
drwxr-xr-x 3 107 114 4.0K Oct 19 15:53 .
drwxr-xr-x 5 107 114 4.0K Oct 20 13:11 ..
-rw-r--r-- 1 107 114  311 Oct 19 15:53 Dockerfile
drwxr-xr-x 8 107 114 4.0K Oct 20 14:04 .git
-rw-r--r-- 1 107 114   57 Oct 19 15:53 go.mod
-rw-r--r-- 1 107 114  239 Oct 19 15:53 main.go
-rw-r--r-- 1 107 114  175 Oct 19 15:53 main_test.go
-rw-r--r-- 1 107 114 1.8K Oct 19 15:53 README.md
-rw-r--r-- 1 107 114 4.4K Oct 19 15:53 Vagrantfile
+ docker build . -t v99-terra-01:8082/hello-world:v10
Sending build context to Docker daemon  182.8kB

Step 1/8 : FROM golang:1.16 AS builder
 ---> 972d8c0bc0fc
Step 2/8 : WORKDIR $GOPATH/src/github.com/netology-code/sdvps-materials
 ---> Using cache
 ---> 8ebe6cd73fd2
Step 3/8 : COPY . ./
 ---> Using cache
 ---> bd32591c7536
Step 4/8 : RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix nocgo -o /app .
 ---> Using cache
 ---> 01ffa0fa72fd
Step 5/8 : FROM alpine:latest
 ---> 9c6f07244728
Step 6/8 : RUN apk -U add ca-certificates
 ---> Using cache
 ---> 41ac3f2cf3b3
Step 7/8 : COPY --from=builder /app /app
 ---> Using cache
 ---> 9b91134673a4
Step 8/8 : CMD ["/app"]
 ---> Using cache
 ---> a71e5aff17d4
Successfully built a71e5aff17d4
Successfully tagged v99-terra-01:8082/hello-world:v10
[test] $ /bin/sh -xe /tmp/jenkins333144787133496031.sh
+ docker login v99-terra-01:8082 -u admin -p Admin123
WARNING! Using --password via the CLI is insecure. Use --password-stdin.
WARNING! Your password will be stored unencrypted in /var/lib/jenkins/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded
+ docker push v99-terra-01:8082/hello-world:v10
The push refers to repository [v99-terra-01:8082/hello-world]
68e7de1a2cf3: Preparing
4689489b60e5: Preparing
994393dc58e7: Preparing
68e7de1a2cf3: Pushed
4689489b60e5: Pushed
994393dc58e7: Pushed
v10: digest: sha256:383c2df2e37cf4fe663ed114ce289ca9902cd0cafa8ba82cdfe4c0662fe2505f size: 950
+ docker logout
Removing login credentials for https://index.docker.io/v1/
Finished: SUCCESS
```
![img_2.png](img_2.png)



### 2. Второе задание
```angular2html
Started by user DVakhrameev
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in /var/lib/jenkins/workspace/test2
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Git)
[Pipeline] git
The recommended git tool is: NONE
No credentials specified
 > git rev-parse --resolve-git-dir /var/lib/jenkins/workspace/test2/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/netology-code/sdvps-materials.git # timeout=10
Fetching upstream changes from https://github.com/netology-code/sdvps-materials.git
 > git --version # timeout=10
 > git --version # 'git version 2.30.2'
 > git fetch --tags --force --progress -- https://github.com/netology-code/sdvps-materials.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/master^{commit} # timeout=10
Checking out Revision da5acf7bcb7f437637adf06fbd03a24dc2c8f13e (refs/remotes/origin/master)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f da5acf7bcb7f437637adf06fbd03a24dc2c8f13e # timeout=10
 > git branch -a -v --no-abbrev # timeout=10
 > git branch -D master # timeout=10
 > git checkout -b master da5acf7bcb7f437637adf06fbd03a24dc2c8f13e # timeout=10
Commit message: "branch main, add creds for vagrant box"
 > git rev-list --no-walk da5acf7bcb7f437637adf06fbd03a24dc2c8f13e # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Test)
[Pipeline] sh
+ /usr/local/go/bin/go test .
ok  	github.com/netology-code/sdvps-materials	(cached)
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Build)
[Pipeline] sh
+ docker build . -t v99-terra-01:8082/hello-world:v8
Sending build context to Docker daemon    277kB

Step 1/8 : FROM golang:1.16 AS builder
 ---> 972d8c0bc0fc
Step 2/8 : WORKDIR $GOPATH/src/github.com/netology-code/sdvps-materials
 ---> Using cache
 ---> 8ebe6cd73fd2
Step 3/8 : COPY . ./
 ---> 74df22f1dbbe
Step 4/8 : RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix nocgo -o /app .
 ---> Running in e76b17697fc7
Removing intermediate container e76b17697fc7
 ---> 97bd362f9073
Step 5/8 : FROM alpine:latest
 ---> 9c6f07244728
Step 6/8 : RUN apk -U add ca-certificates
 ---> Using cache
 ---> 41ac3f2cf3b3
Step 7/8 : COPY --from=builder /app /app
 ---> Using cache
 ---> 9b91134673a4
Step 8/8 : CMD ["/app"]
 ---> Using cache
 ---> a71e5aff17d4
Successfully built a71e5aff17d4
Successfully tagged v99-terra-01:8082/hello-world:v8
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Push)
[Pipeline] sh
+ docker login v99-terra-01:8082 -u admin -p Admin
WARNING! Using --password via the CLI is insecure. Use --password-stdin.
WARNING! Your password will be stored unencrypted in /var/lib/jenkins/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded
+ docker push v99-terra-01:8082/hello-world:v8
The push refers to repository [v99-terra-01:8082/hello-world]
68e7de1a2cf3: Preparing
4689489b60e5: Preparing
994393dc58e7: Preparing
994393dc58e7: Layer already exists
4689489b60e5: Layer already exists
68e7de1a2cf3: Layer already exists
v8: digest: sha256:383c2df2e37cf4fe663ed114ce289ca9902cd0cafa8ba82cdfe4c0662fe2505f size: 950
+ docker logout
Removing login credentials for https://index.docker.io/v1/
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```
Pipeline
```angular2html
pipeline {
 agent any
 stages {
  stage('Git') {
   steps {git 'https://github.com/netology-code/sdvps-materials.git'}
  }
  stage('Test') {
   steps {
    sh '/usr/local/go/bin/go test .'
   }
  }
  stage('Build') {
   steps {
    sh 'docker build . -t v99-terra-01:8082/hello-world:v$BUILD_NUMBER'
   }
  }
  stage('Push') {
   steps {
    sh 'docker login v99-terra-01:8082 -u admin -p Admin && docker push v99-terra-01:8082/hello-world:v$BUILD_NUMBER && docker logout'   }
  }
 }
}
```
![img_1.png](img_1.png)

### 3. Третье задание
```angular2html
Started by user DVakhrameev
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in /var/lib/jenkins/workspace/test2
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Git)
[Pipeline] git
The recommended git tool is: NONE
No credentials specified
 > git rev-parse --resolve-git-dir /var/lib/jenkins/workspace/test2/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/kozl/netology-devops.git # timeout=10
Fetching upstream changes from https://github.com/kozl/netology-devops.git
 > git --version # timeout=10
 > git --version # 'git version 2.30.2'
 > git fetch --tags --force --progress -- https://github.com/kozl/netology-devops.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/master^{commit} # timeout=10
Checking out Revision 97022ff69409ecfa375e31d3bbc610bd8c3f6f86 (refs/remotes/origin/master)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 97022ff69409ecfa375e31d3bbc610bd8c3f6f86 # timeout=10
 > git branch -a -v --no-abbrev # timeout=10
 > git branch -D master # timeout=10
 > git checkout -b master 97022ff69409ecfa375e31d3bbc610bd8c3f6f86 # timeout=10
Commit message: "delete teamcity dir"
 > git rev-list --no-walk 97022ff69409ecfa375e31d3bbc610bd8c3f6f86 # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Test)
[Pipeline] sh
+ /usr/local/go/bin/go test .
ok  	github.com/kozl/netology-devops	(cached)
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Build)
[Pipeline] sh
+ CGO_ENABLED=0 GOOS=linux /usr/local/go/bin/go build -a -installsuffix nocgo -o /tmp/app-v24 .
[Pipeline] sh
+ curl -u admin:Admin123 http://192.168.56.149:8081/repository/test2/ --upload-file /tmp/app-v24 -vv
*   Trying 192.168.56.149:8081...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed

  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* Connected to 192.168.56.149 (192.168.56.149) port 8081 (#0)
* Server auth using Basic with user 'admin'
> PUT /repository/test2/app-v24 HTTP/1.1
> Host: 192.168.56.149:8081
> Authorization: Basic YWRtaW46R25vbWlLYWthMzQ=
> User-Agent: curl/7.74.0
> Accept: */*
> Content-Length: 1923898
> Expect: 100-continue
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 100 Continue
} [65536 bytes data]
* We are completely uploaded and fine
* Mark bundle as not supporting multiuse
< HTTP/1.1 201 Created
< Date: Thu, 20 Oct 2022 13:50:14 GMT
< Server: Nexus/3.42.0-01 (OSS)
< X-Content-Type-Options: nosniff
< Content-Security-Policy: sandbox allow-forms allow-modals allow-popups allow-presentation allow-scripts allow-top-navigation
< X-XSS-Protection: 1; mode=block
< Content-Length: 0
< 

100 1878k    0     0  100 1878k      0  76.4M --:--:-- --:--:-- --:--:-- 76.4M
* Connection #0 to host 192.168.56.149 left intact
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS

```

```angular2html
pipeline {
 agent any
 stages {
  stage('Git') {
   steps {git 'https://github.com/kozl/netology-devops.git'}
  }
  stage('Test') {
   steps {
    sh '/usr/local/go/bin/go test .'
   }
  }
  stage('Build') {
   steps {
	sh 'CGO_ENABLED=0 GOOS=linux /usr/local/go/bin/go build -a -installsuffix nocgo -o /tmp/app-v$BUILD_NUMBER .'
    sh 'curl -u admin:Admin123 http://192.168.56.149:8081/repository/test2/ --upload-file /tmp/app-v$BUILD_NUMBER -vv'
   }
  }
 }
}

```

![img_3.png](img_3.png)