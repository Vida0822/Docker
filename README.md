#### Team Notion 



#### Code 
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

##### 이미지 

```bash
docker image pull diamol/ch03-web-ping
```


### 도커 허브 

```bash
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

새로운 크로스 플랫폼 PowerShell 사용 https://aka.ms/pscore6

PS C:\Users\SHIN HEEMIN> docker

Usage:  docker [OPTIONS] COMMAND

A self-sufficient runtime for containers

Common Commands:
  run         Create and run a new container from an image
  exec        Execute a command in a running container
  ps          List containers
  build       Build an image from a Dockerfile
  pull        Download an image from a registry
  push        Upload an image to a registry
  images      List images
  login       Log in to a registry
  logout      Log out from a registry
  search      Search Docker Hub for images
  version     Show the Docker version information
  info        Display system-wide information

Management Commands:
  builder     Manage builds
  buildx*     Docker Buildx
  compose*    Docker Compose
  container   Manage containers
  context     Manage contexts
  debug*      Get a shell into any image or container
  desktop*    Docker Desktop commands (Alpha)
  dev*        Docker Dev Environments
  extension*  Manages Docker extensions
  feedback*   Provide feedback, right in your terminal!
  image       Manage images
  init*       Creates Docker-related starter files for your project
  manifest    Manage Docker image manifests and manifest lists
  network     Manage networks
  plugin      Manage plugins
  sbom*       View the packaged-based Software Bill Of Materials (SBOM) for an image
  scout*      Docker Scout
  system      Manage Docker
  trust       Manage trust on Docker images
  volume      Manage volumes

Swarm Commands:
  swarm       Manage Swarm

Commands:
  attach      Attach local standard input, output, and error streams to a running container
  commit      Create a new image from a container's changes
  cp          Copy files/folders between a container and the local filesystem
  create      Create a new container
  diff        Inspect changes to files or directories on a container's filesystem
  events      Get real time events from the server
  export      Export a container's filesystem as a tar archive
  history     Show the history of an image
  import      Import the contents from a tarball to create a filesystem image
  inspect     Return low-level information on Docker objects
  kill        Kill one or more running containers
  load        Load an image from a tar archive or STDIN
  logs        Fetch the logs of a container
  pause       Pause all processes within one or more containers
  port        List port mappings or a specific mapping for the container
  rename      Rename a container
  restart     Restart one or more containers
  rm          Remove one or more containers
  rmi         Remove one or more images
  save        Save one or more images to a tar archive (streamed to STDOUT by default)
  start       Start one or more stopped containers
  stats       Display a live stream of container(s) resource usage statistics
  stop        Stop one or more running containers
  unpause     Unpause all processes within one or more containers
  wait        Block until one or more containers stop, then print their exit codes

Global Options:
                           "C:\\Users\\SHIN HEEMIN\\.docker")
  -c, --context string     Name of the context to use to connect to the
                           daemon (overrides DOCKER_HOST env var and
  -D, --debug              Enable debug mode
  -H, --host list          Daemon socket to connect to
  -l, --log-level string   Set the logging level ("debug", "info",
      --tls                Use TLS; implied by --tlsverify
      --tlscacert string   Trust certs signed only by this CA (default
                           "C:\\Users\\SHIN HEEMIN\\.docker\\ca.pem")
                           "C:\\Users\\SHIN HEEMIN\\.docker\\cert.pem")
      --tlskey string      Path to TLS key file (default "C:\\Users\\SHIN
                           HEEMIN\\.docker\\key.pem")
  -v, --version            Print version information and quit

Run 'docker COMMAND --help' for more information on a command.
For more help on how to use Docker, head to https://docs.docker.com/go/guides/
PS C:\Users\SHIN HEEMIN> echo $dockerId
heemin0822
PS C:\Users\SHIN HEEMIN> docker login --username $dockerId
Password:

PS C:\Users\SHIN HEEMIN> docker login --username $dockerId

Error response from daemon: Get "https://registry-1.docker.io/v2/": unauthorized: incorrect username or password
PS C:\Users\SHIN HEEMIN> docker login --username $dockerId
Password:

Error response from daemon: Get "https://registry-1.docker.io/v2/": unauthorized: incorrect username or password
PS C:\Users\SHIN HEEMIN> docker login --username Heemin0822
Password:
Error response from daemon: Get "https://registry-1.docker.io/v2/": unauthorized: incorrect username or password
PS C:\Users\SHIN HEEMIN> docker login --username Heemin0822
Password:

Error response from daemon: Get "https://registry-1.docker.io/v2/": unauthorized: incorrect username or password
PS C:\Users\SHIN HEEMIN> docker login --username $dockerId
Password:

Login Succeeded
PS C:\Users\SHIN HEEMIN> docker image tag image-gallery $dockerId/image-gallery:v1
Error response from daemon: No such image: image-gallery:latest
PS C:\Users\SHIN HEEMIN> docker image pull diamol/ch03-web-ping
Using default tag: latest
latest: Pulling from diamol/ch03-web-ping
Digest: sha256:2f2dce710a7f287afc2d7bbd0d68d024bab5ee37a1f658cef46c64b1a69affd2
Status: Image is up to date for diamol/ch03-web-ping:latest
docker.io/diamol/ch03-web-ping:latest
PS C:\Users\SHIN HEEMIN> docker image tag ch03-web-ping $dockerId/ch03-web-ping:v1
Error response from daemon: No such image: ch03-web-ping:latest
PS C:\Users\SHIN HEEMIN> cd ch03/exercises/web-ping
cd : 'C:\Users\SHIN HEEMIN\ch03\exercises\web-ping' 경로는 존재하지 않으므로 찾을 수 없습니다.
위치 줄:1 문자:1
+ cd ch03/exercises/web-ping
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (C:\Users\SHIN H...rcises\web-ping:String) [Set-Location], ItemNotFoundE
   xception
    + FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.SetLocationCommand

PS C:\Users\SHIN HEEMIN> docker info
Client:
 Version:    27.0.3
 Context:    desktop-linux
 Debug Mode: false
 Plugins:
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.15.1-desktop.1
    Path:     C:\Program Files\Docker\cli-plugins\docker-buildx.exe
  compose: Docker Compose (Docker Inc.)
    Version:  v2.28.1-desktop.1
    Path:     C:\Program Files\Docker\cli-plugins\docker-compose.exe
  debug: Get a shell into any image or container (Docker Inc.)
    Version:  0.0.32
    Path:     C:\Program Files\Docker\cli-plugins\docker-debug.exe
  desktop: Docker Desktop commands (Alpha) (Docker Inc.)
    Version:  v0.0.14
    Path:     C:\Program Files\Docker\cli-plugins\docker-desktop.exe
  dev: Docker Dev Environments (Docker Inc.)
    Version:  v0.1.2
    Path:     C:\Program Files\Docker\cli-plugins\docker-dev.exe
  extension: Manages Docker extensions (Docker Inc.)
    Version:  v0.2.25
    Path:     C:\Program Files\Docker\cli-plugins\docker-extension.exe
  feedback: Provide feedback, right in your terminal! (Docker Inc.)
    Version:  v1.0.5
    Path:     C:\Program Files\Docker\cli-plugins\docker-feedback.exe
  init: Creates Docker-related starter files for your project (Docker Inc.)
    Version:  v1.3.0
    Path:     C:\Program Files\Docker\cli-plugins\docker-init.exe
  sbom: View the packaged-based Software Bill Of Materials (SBOM) for an image (Anchore Inc.)
    Version:  0.6.0
    Path:     C:\Program Files\Docker\cli-plugins\docker-sbom.exe
  scout: Docker Scout (Docker Inc.)
    Version:  v1.10.0
    Path:     C:\Program Files\Docker\cli-plugins\docker-scout.exe

Server:
 Containers: 1
  Running: 0
  Paused: 0
  Stopped: 1
 Images: 1
 Server Version: 27.0.3
 Storage Driver: overlay2
  Backing Filesystem: extfs
  Supports d_type: true
  Using metacopy: false
  Native Overlay Diff: true
  userxattr: false
 Logging Driver: json-file
 Cgroup Driver: cgroupfs
 Cgroup Version: 1
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 Swarm: inactive
 Runtimes: runc io.containerd.runc.v2
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: ae71819c4f5e67bb4d5ae76a6b735f29cc25774e
 runc version: v1.1.13-0-g58aa920
 init version: de40ad0
  seccomp
   Profile: unconfined
 Kernel Version: 5.15.153.1-microsoft-standard-WSL2
 Operating System: Docker Desktop
 OSType: linux
 Architecture: x86_64
 CPUs: 4
 Name: docker-desktop
 ID: d8accbc8-3a5c-4a76-8802-1d2efd616418
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 HTTP Proxy: http.docker.internal:3128
 HTTPS Proxy: http.docker.internal:3128
 No Proxy: hubproxy.docker.internal
 Insecure Registries:
  hubproxy.docker.internal:5555
  127.0.0.0/8
 Live Restore Enabled: false

WARNING: No blkio throttle.read_bps_device support
WARNING: No blkio throttle.write_bps_device support
WARNING: No blkio throttle.write_iops_device support
WARNING: daemon is not using the default seccomp profile
PS C:\Users\SHIN HEEMIN> cd /var/lib/docker
cd : 'C:\var\lib\docker' 경로는 존재하지 않으므로 찾을 수 없습니다.
위치 줄:1 문자:1
+ cd /var/lib/docker
+ ~~~~~~~~~~~~~~~~~~
    + FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.SetLocationCommand

PS C:\Users\SHIN HEEMIN> cd D:\docker practice\080258
Set-Location : 'practice\080258' 인수를 허용하는 위치 매개 변수를 찾을 수 없습니다.
위치 줄:1 문자:1
+ cd D:\docker practice\080258
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SetLocationCommand

PS C:\Users\SHIN HEEMIN> cd ../
PS C:\Users> cd D:\
PS D:\> cd \docker practice\080258
Set-Location : 'practice\080258' 인수를 허용하는 위치 매개 변수를 찾을 수 없습니다.
위치 줄:1 문자:1

PS D:\> cd docker practice\080258
Set-Location : 'practice\080258' 인수를 허용하는 위치 매개 변수를 찾을 수 없습니다.
위치 줄:1 문자:1
+ cd docker practice\080258
+ ~~~~~~~~~~~~~~~~~~~~~~~~~
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SetLocationCommand

PS D:\> cd docker practive
Set-Location : 'practive' 인수를 허용하는 위치 매개 변수를 찾을 수 없습니다.
위치 줄:1 문자:1
+ cd docker practive
+ ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Set-Location], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SetLocationCommand

PS D:\> cd docker practice
Set-Location : 'practice' 인수를 허용하는 위치 매개 변수를 찾을 수 없습니다.
위치 줄:1 문자:1
+ cd docker practice
+ ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Set-Location], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SetLocationCommand

PS D:\> cd docker_practice
PS D:\docker_practice> cd 080258
PS D:\docker_practice\080258> cd ch03/exercises/web-ping
PS D:\docker_practice\080258\ch03\exercises\web-ping> docker image build --tag web-ping
ERROR: "docker buildx build" requires exactly 1 argument.

PS D:\docker_practice\080258\ch03\exercises\web-ping> docker image build --tag web-ping .
[+] Building 9.4s (9/9) FINISHED                                                                   docker:desktop-linux
 => [internal] load build definition from Dockerfile                                                               0.0s
 => => transferring dockerfile: 200B                                                                               0.0s
 => [internal] load metadata for docker.io/diamol/node:latest                                                      8.5s
 => [auth] diamol/node:pull token for registry-1.docker.io                                                         0.0s
 => [internal] load .dockerignore                                                                                  0.1s
 => => transferring context: 2B                                                                                    0.0s
 => [1/3] FROM docker.io/diamol/node:latest@sha256:dfee522acebdfdd9964aa9c88ebebd03a20b6dd573908347be3ebf52ac4879  0.3s
 => => resolve docker.io/diamol/node:latest@sha256:dfee522acebdfdd9964aa9c88ebebd03a20b6dd573908347be3ebf52ac4879  0.1s
 => => sha256:dfee522acebdfdd9964aa9c88ebebd03a20b6dd573908347be3ebf52ac4879c8 1.41kB / 1.41kB                     0.0s
 => => sha256:f59303fb3248e5d992586c76cc83e1d3700f641cbcd7c0067bc7ad5bb2e5b489 1.16kB / 1.16kB                     0.0s
 => => sha256:9dfa73010b19a67a86f360868c0f50fff7b5e6d4fd76d21df822c62aa784f810 5.66kB / 5.66kB                     0.0s
 => => transferring context: 881B                                                                                  0.0s
 => [2/3] WORKDIR /web-ping                                                                                        0.1s
 => exporting to image                                                                                             0.1s
 => => writing image sha256:83119e8bc7d9b666ff821855030bdf7c630aa150c2fdd67417037991a89d5198                       0.0s
 => => naming to docker.io/library/web-ping                                                                        0.0s

What's next:
    View a summary of image vulnerabilities and recommendations → docker scout quickview
PS D:\docker_practice\080258\ch03\exercises\web-ping> docker image tag web-ping $dockerId/web-ping:v1
PS D:\docker_practice\080258\ch03\exercises\web-ping> docker image ls --filter reference=image-gallery --filter reference='*/webp'                                                                                                              PS D:\docker_practice\080258\ch03\exercises\web-ping> docker image push $dockerId/image-gallery:v1
An image does not exist locally with the tag: heemin0822/image-gallery








                                                      docker image ls --filter reference=image-gallery --filter reference='*/webp'
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
PS D:\docker_practice\080258\ch03\exercises\web-ping> docker image ls --filter reference=image-gallery --filter reference='*/webp'
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
PS D:\docker_practice\080258\ch03\exercises\web-ping> docker image push $dockerId/web-ping:v1
The push refers to repository [docker.io/heemin0822/web-ping]
e432e0ec1e3b: Pushed
109c4a769edd: Mounted from diamol/node
04db5bd8a39f: Mounted from diamol/node
eaa2fd82d1ac: Mounted from diamol/node
f1b5933fe4b5: Mounted from diamol/node
v1: digest: sha256:b3e4c6c331b3e6642b5c9661d2f9c4511fad3c734760fb3fef650b1d47bb2cdb size: 1571
PS D:\docker_practice\080258\ch03\exercises\web-ping> echo "https://hub.docker.com/r/$dockerId/image-gallery/tags"
https://hub.docker.com/r/heemin0822/image-gallery/tags
PS D:\docker_practice\080258\ch03\exercises\web-ping> echo "https://hub.docker.com/r/$dockerId/web-ping/tags"
https://hub.docker.com/r/heemin0822/web-ping/tags
docke : 'docke' 용어가 cmdlet, 함수, 스크립트 파일 또는 실행할 수 있는 프로그램 이름으로 인식되지 않습니다. 이름이 정확
한지 확인하고 경로가 포함된 경우 경로가 올바른지 검증한 다음 다시 시도하십시오.
위치 줄:1 문자:1
+ docke container run -d -p 5000:5000 --restart diampl/registry
+ ~~~~~
    + CategoryInfo          : ObjectNotFound: (docke:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException

PS D:\docker_practice\080258\ch03\exercises\web-ping> docke container run -d -p 5000:5000 --restart diamol/registry
docke : 'docke' 용어가 cmdlet, 함수, 스크립트 파일 또는 실행할 수 있는 프로그램 이름으로 인식되지 않습니다. 이름이 정확
한지 확인하고 경로가 포함된 경우 경로가 올바른지 검증한 다음 다시 시도하십시오.
+ ~~~~~
    + CategoryInfo          : ObjectNotFound: (docke:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException

PS D:\docker_practice\080258\ch03\exercises\web-ping> docke container run -d -p 5000:5000 --restart always diamol/registry
docke : 'docke' 용어가 cmdlet, 함수, 스크립트 파일 또는 실행할 수 있는 프로그램 이름으로 인식되지 않습니다. 이름이 정확
한지 확인하고 경로가 포함된 경우 경로가 올바른지 검증한 다음 다시 시도하십시오.
+ docke container run -d -p 5000:5000 --restart always diamol/registry
    + FullyQualifiedErrorId : CommandNotFoundException

PS D:\docker_practice\080258\ch03\exercises\web-ping> docker container run -d -p 5000:5000 --restart always diamol/registry
Unable to find image 'diamol/registry:latest' locally
latest: Pulling from diamol/registry
31603596830f: Pull complete
792f5419a843: Pull complete
3fec9ac2e0fe: Pull complete
b72408f4bc4f: Pull complete
6a2aeb3b52c0: Pull complete
Digest: sha256:49c5a928c870d496013d98d4357c93f35b1896a0385ef275664bc43e69b14950
Status: Downloaded newer image for diamol/registry:latest
a1da6f7abe94e6c47585ec7e5bd6092bc63a8e53248227c11932aa67c957cffd
PS D:\docker_practice\080258\ch03\exercises\web-ping> Add-Content -Value "127.0.0.1 registry.local" -Path /windows/system32/drivers/etc/hosts                                                                                                   Add-Content : 'D:\windows\system32\drivers\etc\hosts' 경로의 일부를 찾을 수 없습니다.
위치 줄:1 문자:1
+ Add-Content -Value "127.0.0.1 registry.local" -Path /windows/system32 ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (D:\windows\system32\drivers\etc\hosts:String) [Add-Content], DirectoryN
   otFoundException
    + FullyQualifiedErrorId : GetContentWriterDirectoryNotFoundError,Microsoft.PowerShell.Commands.AddContentCommand

PS D:\docker_practice\080258\ch03\exercises\web-ping> docker image tag webp localhost:5000/webp/ui:v1
Error response from daemon: No such image: webp:latest
PS D:\docker_practice\080258\ch03\exercises\web-ping> docker image tag web-ping localhost:5000/web-ping/ui:v1
PS D:\docker_practice\080258\ch03\exercises\web-ping> localhost:5000/web-ping/ui:v1
localhost:5000/web-ping/ui:v1 : 'localhost:5000/web-ping/ui:v1' 용어가 cmdlet, 함수, 스크립트 파일 또는 실행할 수 있는
프로그램 이름으로 인식되지 않습니다. 이름이 정확한지 확인하고 경로가 포함된 경우 경로가 올바른지 검증한 다음 다시 시도
하십시오.
위치 줄:1 문자:1
+ localhost:5000/web-ping/ui:v1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (localhost:5000/web-ping/ui:v1:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException

PS D:\docker_practice\080258\ch03\exercises\web-ping> docker info
Client:
 Version:    27.0.3
 Context:    desktop-linux
 Debug Mode: false
 Plugins:
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.15.1-desktop.1
    Path:     C:\Program Files\Docker\cli-plugins\docker-buildx.exe
  compose: Docker Compose (Docker Inc.)
    Version:  v2.28.1-desktop.1
    Path:     C:\Program Files\Docker\cli-plugins\docker-compose.exe
  debug: Get a shell into any image or container (Docker Inc.)
    Version:  0.0.32
    Path:     C:\Program Files\Docker\cli-plugins\docker-debug.exe
  desktop: Docker Desktop commands (Alpha) (Docker Inc.)
    Version:  v0.0.14
    Path:     C:\Program Files\Docker\cli-plugins\docker-desktop.exe
  dev: Docker Dev Environments (Docker Inc.)
    Version:  v0.1.2
    Path:     C:\Program Files\Docker\cli-plugins\docker-dev.exe
  extension: Manages Docker extensions (Docker Inc.)
    Version:  v0.2.25
    Path:     C:\Program Files\Docker\cli-plugins\docker-extension.exe
  feedback: Provide feedback, right in your terminal! (Docker Inc.)
    Version:  v1.0.5
    Path:     C:\Program Files\Docker\cli-plugins\docker-feedback.exe
  init: Creates Docker-related starter files for your project (Docker Inc.)
    Version:  v1.3.0
    Path:     C:\Program Files\Docker\cli-plugins\docker-init.exe
  sbom: View the packaged-based Software Bill Of Materials (SBOM) for an image (Anchore Inc.)
    Version:  0.6.0
    Path:     C:\Program Files\Docker\cli-plugins\docker-sbom.exe
  scout: Docker Scout (Docker Inc.)
    Version:  v1.10.0
    Path:     C:\Program Files\Docker\cli-plugins\docker-scout.exe

Server:
 Containers: 3
  Running: 2
  Paused: 0
  Stopped: 1
 Images: 3
 Server Version: 27.0.3
 Storage Driver: overlay2
  Backing Filesystem: extfs
  Supports d_type: true
  Using metacopy: false
  Native Overlay Diff: true
  userxattr: false
 Logging Driver: json-file
 Cgroup Driver: cgroupfs
 Cgroup Version: 1
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 Swarm: inactive
 Runtimes: io.containerd.runc.v2 runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: ae71819c4f5e67bb4d5ae76a6b735f29cc25774e
 runc version: v1.1.13-0-g58aa920
 init version: de40ad0
 Security Options:
   Profile: unconfined
 Kernel Version: 5.15.153.1-microsoft-standard-WSL2
 Operating System: Docker Desktop
 OSType: linux
 Architecture: x86_64
 CPUs: 4
 Total Memory: 3.776GiB
 Name: docker-desktop
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 HTTP Proxy: http.docker.internal:3128
 HTTPS Proxy: http.docker.internal:3128
 No Proxy: hubproxy.docker.internal
 Labels:
  com.docker.desktop.address=npipe://\\.\pipe\docker_cli
 Experimental: false
 Live Restore Enabled: false

WARNING: No blkio throttle.read_bps_device support
WARNING: No blkio throttle.write_bps_device support
WARNING: No blkio throttle.read_iops_device support
WARNING: No blkio throttle.write_iops_device support
WARNING: daemon is not using the default seccomp profile
PS D:\docker_practice\080258\ch03\exercises\web-ping> docker image push localhost:5000/web-ping/ui:v1
The push refers to repository [localhost:5000/web-ping/ui]
e432e0ec1e3b: Pushed
ca7072e93d1a: Pushed
109c4a769edd: Pushed
04db5bd8a39f: Pushed
eaa2fd82d1ac: Pushed
f1b5933fe4b5: Pushed
v1: digest: sha256:b3e4c6c331b3e6642b5c9661d2f9c4511fad3c734760fb3fef650b1d47bb2cdb size: 1571
PS D:\docker_practice\080258\ch03\exercises\web-ping> docker image push localhost:5000/web-ping/ui:v1
The push refers to repository [localhost:5000/web-ping/ui]
e432e0ec1e3b: Layer already exists
ca7072e93d1a: Layer already exists
109c4a769edd: Layer already exists
04db5bd8a39f: Layer already exists
eaa2fd82d1ac: Layer already exists
f1b5933fe4b5: Layer already exists
v1: digest: sha256:b3e4c6c331b3e6642b5c9661d2f9c4511fad3c734760fb3fef650b1d47bb2cdb size: 1571
PS D:\docker_practice\080258\ch03\exercises\web-ping> docker image tag web-ping localhost:5000/web-ping:latest
PS D:\docker_practice\080258\ch03\exercises\web-ping> docker image tag web-ping localhost:5000/web-ping:2
PS D:\docker_practice\080258\ch03\exercises\web-ping> docker image tag web-ping localhost:5000/web-ping:2.1
PS D:\docker_practice\080258\ch03\exercises\web-ping> docker image tag web-ping localhost:5000/web-ping:2.1.106
PS D:\docker_practice\080258\ch03\exercises\web-ping>
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

새로운 크로스 플랫폼 PowerShell 사용 https://aka.ms/pscore6

PS D:\docker_practice\080258> cd ch05/exercises/dotnet-sdk
PS D:\docker_practice\080258\ch05\exercises\dotnet-sdk> ccd ../aspnet-runtime
ccd : 'ccd' 용어가 cmdlet, 함수, 스크립트 파일 또는 실행할 수 있는 프로그램 이름으로 인식되지 않습니다. 이름이 정확한지
 확인하고 경로가 포함된 경우 경로가 올바른지 검증한 다음 다시 시도하십시오.
위치 줄:1 문자:1
+ ccd ../aspnet-runtime
+ ~~~
    + CategoryInfo          : ObjectNotFound: (ccd:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException

PS D:\docker_practice\080258\ch05\exercises\dotnet-sdk> cd ../aspnet-runtime
PS D:\docker_practice\080258\ch05\exercises\aspnet-runtime> docker image build -t golden/aspnet-core:3.0
ERROR: "docker buildx build" requires exactly 1 argument.
See 'docker buildx build --help'.

Usage:  docker buildx build [OPTIONS] PATH | URL | -

Start a build
PS D:\docker_practice\080258\ch05\exercises\aspnet-runtime>
```

##### 로그인
```bash
PS C:\Users\SHIN HEEMIN> docker login --username $dockerId
Password:

Login Succeeded
```
