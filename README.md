# Illustration that @nx-tools/nx-docker is broken

## Preamble

Docker must be installed and running on the development system.

For this project I have been using:
- Docker Engine: 20.10.8
- MacOS Big Sur 11.5.2
- Node: v16.1.0
- Npm: 7.21.1
- Nx: 12.9.0

## Setup

1. Check out this repo: https://github.com/kuccello/example-nx-docker-issue
2. cd into the checked out repo locally: cd example-nx-docker-issue
3. > npm i
4. execute the build of the singe app project: nx run hackathon-api:docker --verbose

TERMINAL OUTPUT:

```bash
> nx run hackathon-api:docker --verbose
::group::Docker info
[command]/usr/local/bin/docker version
Client:
 Cloud integration: 1.0.17
 Version:           20.10.8
 API version:       1.41
 Go version:        go1.16.6
 Git commit:        3967b7d
 Built:             Fri Jul 30 19:55:20 2021
 OS/Arch:           darwin/arm64
 Context:           default
 Experimental:      true

Server: Docker Engine - Community
 Engine:
  Version:          20.10.8
  API version:      1.41 (minimum version 1.12)
  Go version:       go1.16.6
  Git commit:       75249d8
  Built:            Fri Jul 30 19:53:34 2021
  OS/Arch:          linux/arm64
  Experimental:     false
 containerd:
  Version:          1.4.9
  GitCommit:        e25210fe30a0a703442421b0f60afac609f950a3
 runc:
  Version:          1.0.1
  GitCommit:        v1.0.1-0-g4144b63
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0
[command]/usr/local/bin/docker info
Client:
 Context:    default
 Debug Mode: false
 Plugins:
  buildx: Build with BuildKit (Docker Inc., v0.6.1-docker)
  compose: Docker Compose (Docker Inc., v2.0.0-rc.1)
  scan: Docker Scan (Docker Inc., v0.8.0)

Server:
 Containers: 3
  Running: 0
  Paused: 0
  Stopped: 3
 Images: 3
 Server Version: 20.10.8
 Storage Driver: overlay2
  Backing Filesystem: extfs
  Supports d_type: true
  Native Overlay Diff: true
  userxattr: false
 Logging Driver: json-file
 Cgroup Driver: cgroupfs
 Cgroup Version: 1
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local logentries splunk syslog
 Swarm: inactive
 Runtimes: io.containerd.runc.v2 io.containerd.runtime.v1.linux runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: e25210fe30a0a703442421b0f60afac609f950a3
 runc version: v1.0.1-0-g4144b63
 init version: de40ad0
 Security Options:
  seccomp
   Profile: default
 Kernel Version: 5.10.47-linuxkit
 Operating System: Docker Desktop
 OSType: linux
 Architecture: aarch64
 CPUs: 4
 Total Memory: 1.942GiB
 Name: docker-desktop
 ID: RJLY:P2PW:LT4O:JJOR:VSFV:XSNP:7UDL:GTW2:GWIL:4RJM:QWWV:YR56
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 HTTP Proxy: http.docker.internal:3128
 HTTPS Proxy: http.docker.internal:3128
 Registry: https://index.docker.io/v1/
 Labels:
 Experimental: false
 Insecure Registries:
  127.0.0.0/8
 Live Restore Enabled: false

::endgroup::
Starting build...
::debug::executing -> docker buildx build --iidfile /var/folders/36/m7bk9rjn2637hkt0drhkd36r0000gn/T/docker-build-push-rp8CZW/iidfile .
[command]/usr/local/bin/docker buildx build --iidfile /var/folders/36/m7bk9rjn2637hkt0drhkd36r0000gn/T/docker-build-push-rp8CZW/iidfile .
#1 [internal] load build definition from Dockerfile
#1 transferring dockerfile: 2B done
#1 DONE 0.0s
error: failed to solve: failed to solve with frontend dockerfile.v0: failed to read dockerfile: open /var/lib/docker/tmp/buildkit-mount482450846/Dockerfile: no such file or directory
buildx call failed with: error: failed to solve: failed to solve with frontend dockerfile.v0: failed to read dockerfile: open /var/lib/docker/tmp/buildkit-mount482450846/Dockerfile: no such file or directory
Error: buildx call failed with: error: failed to solve: failed to solve with frontend dockerfile.v0: failed to read dockerfile: open /var/lib/docker/tmp/buildkit-mount482450846/Dockerfile: no such file or directory
    at /Users/kristanuccello/Development/Projects/com.emergentbit/node_modules/@nx-tools/nx-docker/src/executors/build/main.js:38:23
    at processTicksAndRejections (node:internal/process/task_queues:96:5)

———————————————————————————————————————————————

>  NX   ERROR  Running target "hackathon-api:docker" failed

  Failed tasks:

  - hackathon-api:docker

  Hint: run the command with --verbose for more details.
```