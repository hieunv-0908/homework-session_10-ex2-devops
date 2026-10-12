\# Bài 2: Đóng gói ứng dụng Web Backend bằng Single-stage Dockerfile



Dự án này thực hiện đóng gói ứng dụng Node.js/Express Web API đơn giản thành Docker Image bằng kĩ thuật Single-stage build.



\## Hướng dẫn chạy \& Kiểm tra



\### 1. Xây dựng Docker Image

Mở terminal tại thư mục `homework/session\_10/ex2/` và chạy lệnh:

```bash

docker build -t hw-backend:v1 .



----------------------------


Làm việc trên CLI:


Microsoft Windows [Version 10.0.26300.9550]
(c) Microsoft Corporation. All rights reserved.

D:\baitap_devops\baitap\ss10\b2>docker run -d --name app-single-stage -p 8080:3000 hw-backend:v1
Unable to find image 'hw-backend:v1' locally

What's next:
    Debug this container error with Gordon → docker ai "help me fix this container error"
docker: Error response from daemon: pull access denied for hw-backend, repository does not exist or may require 'docker login'

Run 'docker run --help' for more information

D:\baitap_devops\baitap\ss10\b2>dir
 Volume in drive D has no label.
 Volume Serial Number is 1570-C310

 Directory of D:\baitap_devops\baitap\ss10\b2

13/10/2026  03:22 SA    <DIR>          .
13/10/2026  03:20 SA    <DIR>          ..
13/10/2026  03:21 SA               188 Dockerfile
13/10/2026  03:21 SA               182 package.json
13/10/2026  03:22 SA               452 README.md
13/10/2026  03:22 SA               301 server.js
               4 File(s)          1.123 bytes
               2 Dir(s)   1.859.067.904 bytes free

D:\baitap_devops\baitap\ss10\b2>..
'..' is not recognized as an internal or external command,
operable program or batch file.

D:\baitap_devops\baitap\ss10\b2>docker build -t hw-backend:v1 .
[+] Building 28.1s (11/11) FINISHED                                                                docker:desktop-linux
 => [internal] load build definition from Dockerfile                                                               0.2s
 => => transferring dockerfile: 227B                                                                               0.0s
 => [internal] load metadata for docker.io/library/node:18-alpine                                                  6.3s
 => [auth] library/node:pull token for registry-1.docker.io                                                        0.0s
 => [internal] load .dockerignore                                                                                  0.1s
 => => transferring context: 2B                                                                                    0.0s
 => [1/5] FROM docker.io/library/node:18-alpine@sha256:8d6421d663b4c28fd3ebc498332f249011d118945588d0a35cb9bc4b8c  8.1s
 => => resolve docker.io/library/node:18-alpine@sha256:8d6421d663b4c28fd3ebc498332f249011d118945588d0a35cb9bc4b8c  0.1s
 => => sha256:25ff2da83641908f65c3a74d80409d6b1b62ccfaab220b9ea70b80df5a2e0549 446B / 446B                         0.9s
 => => sha256:1e5a4c89cee5c0826c540ab06d4b6b491c96eda01837f430bd47f0d26702d6e3 1.26MB / 1.26MB                     1.5s
 => => sha256:dd71dde834b5c203d162902e6b8994cb2309ae049a0eabc4efea161b2b5a3d0e 40.01MB / 40.01MB                   5.6s
 => => sha256:f18232174bc91741fdf3da96d85011092101a032a93a388b79e99e69c2d5c870 3.64MB / 3.64MB                     4.1s
 => => extracting sha256:f18232174bc91741fdf3da96d85011092101a032a93a388b79e99e69c2d5c870                          0.4s
 => => extracting sha256:dd71dde834b5c203d162902e6b8994cb2309ae049a0eabc4efea161b2b5a3d0e                          1.7s
 => => extracting sha256:1e5a4c89cee5c0826c540ab06d4b6b491c96eda01837f430bd47f0d26702d6e3                          0.2s
 => => extracting sha256:25ff2da83641908f65c3a74d80409d6b1b62ccfaab220b9ea70b80df5a2e0549                          0.0s
 => [internal] load build context                                                                                  0.3s
 => => transferring context: 1.28kB                                                                                0.1s
 => [2/5] WORKDIR /app                                                                                             1.4s
 => [3/5] COPY package.json package-lock.json* ./                                                                  0.1s
 => [4/5] RUN npm install --only=production                                                                        6.4s
 => [5/5] COPY . .                                                                                                 0.3s
 => exporting to image                                                                                             4.7s
 => => exporting layers                                                                                            3.7s
 => => exporting manifest sha256:32739f0b32df35ca803dfddd3f24c88b63a599e8ad36b18604c1a8c4aa5b7be1                  0.1s
 => => exporting config sha256:279d19887c0690923429e5268320196660fe5e305346f78db48dab16109e7ef4                    0.0s
 => => exporting attestation manifest sha256:f04e6d6eca81f3a036c310ac18ac3ec57327ec1f106e10d947153f2325f47477      0.1s
 => => exporting manifest list sha256:c8dd196d0760aa4cbe62c6f957e3086e853a90af7f21390bf6042def10cea927             0.1s
 => => naming to docker.io/library/hw-backend:v1                                                                   0.0s
 => => unpacking to docker.io/library/hw-backend:v1                                                                0.6s

View build details: docker-desktop://dashboard/build/desktop-linux/desktop-linux/evl8e49uu4um8mj8yqflr58k9

D:\baitap_devops\baitap\ss10\b2>docker run -d --name app-single-stage -p 8080:3000 hw-backend:v1
84cc1167084b6dd56b4b1f90e654ea8ee9a589391e610d36d3bfe0e2d87c5fd8

What's next:
    Debug this container error with Gordon → docker ai "help me fix this container error"
docker: Error response from daemon: ports are not available: exposing port TCP 0.0.0.0:8080 -> 127.0.0.1:0: listen tcp 0.0.0.0:8080: bind: Only one usage of each socket address (protocol/network address/port) is normally permitted.

Run 'docker run --help' for more information

D:\baitap_devops\baitap\ss10\b2>docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

D:\baitap_devops\baitap\ss10\b2>docker run help
Unable to find image 'help:latest' locally

What's next:
    Debug this container error with Gordon → docker ai "help me fix this container error"
docker: Error response from daemon: pull access denied for help, repository does not exist or may require 'docker login'

Run 'docker run --help' for more information

D:\baitap_devops\baitap\ss10\b2>docker run --help
Usage:  docker run [OPTIONS] IMAGE [COMMAND] [ARG...]

Create and run a new container from an image

Aliases:
  docker container run, docker run

Options:
      --add-host list                    Add a custom host-to-IP mapping
                                         (host:ip)
      --annotation map                   Add an annotation to the
                                         container (passed through to the
                                         OCI runtime) (default map[])
  -a, --attach list                      Attach to STDIN, STDOUT or STDERR
      --blkio-weight uint16              Block IO (relative weight),
                                         between 10 and 1000, or 0 to
                                         disable (default 0)
      --blkio-weight-device list         Block IO weight (relative device
                                         weight) (default [])
      --cap-add list                     Add Linux capabilities
      --cap-drop list                    Drop Linux capabilities
      --cgroup-parent string             Optional parent cgroup for the
                                         container
      --cgroupns string                  Cgroup namespace to use
                                         (host|private)
                                         'host':    Run the container in
                                         the Docker host's cgroup
                                         namespace
                                         'private': Run the container in
                                         its own private cgroup namespace
                                         '':        Use the cgroup
                                         namespace as configured by the
                                                    default-cgroupns-mode
                                         option on the daemon (default)
      --cidfile string                   Write the container ID to the file
      --cpu-period int                   Limit CPU CFS (Completely Fair
                                         Scheduler) period
      --cpu-quota int                    Limit CPU CFS (Completely Fair
                                         Scheduler) quota
      --cpu-rt-period int                Limit CPU real-time period in
                                         microseconds
      --cpu-rt-runtime int               Limit CPU real-time runtime in
                                         microseconds
  -c, --cpu-shares int                   CPU shares (relative weight)
      --cpus decimal                     Number of CPUs
      --cpuset-cpus string               CPUs in which to allow execution
                                         (0-3, 0,1)
      --cpuset-mems string               MEMs in which to allow execution
                                         (0-3, 0,1)
  -d, --detach                           Run container in background and
                                         print container ID
      --detach-keys string               Override the key sequence for
                                         detaching a container
      --device list                      Add a host device to the container
      --device-cgroup-rule list          Add a rule to the cgroup allowed
                                         devices list
      --device-read-bps list             Limit read rate (bytes per
                                         second) from a device (default [])
      --device-read-iops list            Limit read rate (IO per second)
                                         from a device (default [])
      --device-write-bps list            Limit write rate (bytes per
                                         second) to a device (default [])
      --device-write-iops list           Limit write rate (IO per second)
                                         to a device (default [])
      --dns list                         Set custom DNS servers
      --dns-option list                  Set DNS options
      --dns-search list                  Set custom DNS search domains
      --domainname string                Container NIS domain name
      --entrypoint string                Overwrite the default ENTRYPOINT
                                         of the image
  -e, --env list                         Set environment variables
      --env-file list                    Read in a file of environment
                                         variables
      --expose list                      Expose a port or a range of ports
      --gpus gpu-request                 GPU devices to add to the
                                         container ('all' to pass all GPUs)
      --group-add list                   Add additional groups to join
      --health-cmd string                Command to run to check health
      --health-interval duration         Time between running the check
                                         (ms|s|m|h) (default 0s)
      --health-retries int               Consecutive failures needed to
                                         report unhealthy
      --health-start-interval duration   Time between running the check
                                         during the start period
                                         (ms|s|m|h) (default 0s)
      --health-start-period duration     Start period for the container
                                         to initialize before starting
                                         health-retries countdown
                                         (ms|s|m|h) (default 0s)
      --health-timeout duration          Maximum time to allow one check
                                         to run (ms|s|m|h) (default 0s)
      --help                             Print usage
  -h, --hostname string                  Container host name
      --init                             Run an init inside the container
                                         that forwards signals and reaps
                                         processes
  -i, --interactive                      Keep STDIN open even if not attached
      --ip ip                            IPv4 address (e.g., 172.30.100.104)
      --ip6 ip                           IPv6 address (e.g., 2001:db8::33)
      --ipc string                       IPC mode to use
      --isolation string                 Container isolation technology
  -l, --label list                       Set meta data on a container
      --label-file list                  Read in a line delimited file of
                                         labels
      --link list                        Add link to another container
      --link-local-ip list               Container IPv4/IPv6 link-local
                                         addresses
      --log-driver string                Logging driver for the container
      --log-opt list                     Log driver options
      --mac-address string               Container MAC address (e.g.,
                                         92:d0:c6:0a:29:33)
  -m, --memory bytes                     Memory limit
      --memory-reservation bytes         Memory soft limit
      --memory-swap bytes                Swap limit equal to memory plus
                                         swap: '-1' to enable unlimited swap
      --memory-swappiness int            Tune container memory swappiness
                                         (0 to 100) (default -1)
      --mount mount                      Attach a filesystem mount to the
                                         container
      --name string                      Assign a name to the container
      --network network                  Connect a container to a network
      --network-alias list               Add network-scoped alias for the
                                         container
      --no-healthcheck                   Disable any container-specified
                                         HEALTHCHECK
      --oom-kill-disable                 Disable OOM Killer
      --oom-score-adj int                Tune host's OOM preferences
                                         (-1000 to 1000)
      --pid string                       PID namespace to use
      --pids-limit int                   Tune container pids limit (set
                                         -1 for unlimited)
      --platform string                  Set platform if server is
                                         multi-platform capable
      --privileged                       Give extended privileges to this
                                         container
  -p, --publish list                     Publish a container's port(s) to
                                         the host
  -P, --publish-all                      Publish all exposed ports to
                                         random ports
      --pull string                      Pull image before running
                                         ("always", "missing", "never")
                                         (default "missing")
  -q, --quiet                            Suppress the pull output
      --read-only                        Mount the container's root
                                         filesystem as read only
      --restart string                   Restart policy to apply when a
                                         container exits (default "no")
      --rm                               Automatically remove the
                                         container and its associated
                                         anonymous volumes when it exits
      --runtime string                   Runtime to use for this container
      --security-opt list                Security Options
      --shm-size bytes                   Size of /dev/shm
      --sig-proxy                        Proxy received signals to the
                                         process (default true)
      --stop-signal string               Signal to stop the container
      --stop-timeout int                 Timeout (in seconds) to stop a
                                         container
      --storage-opt list                 Storage driver options for the
                                         container
      --sysctl map                       Sysctl options (default map[])
      --tmpfs list                       Mount a tmpfs directory
  -t, --tty                              Allocate a pseudo-TTY
      --ulimit ulimit                    Ulimit options (default [])
      --use-api-socket                   Bind mount Docker API socket and
                                         required auth
  -u, --user string                      Username or UID (format:
                                         <name|uid>[:<group|gid>])
      --userns string                    User namespace to use
      --uts string                       UTS namespace to use
  -v, --volume list                      Bind mount a volume
      --volume-driver string             Optional volume driver for the
                                         container
      --volumes-from list                Mount volumes from the specified
                                         container(s)
  -w, --workdir string                   Working directory inside the
                                         container

D:\baitap_devops\baitap\ss10\b2>docker run -d --name app-single-stage -p 8080:3000 hw-backend:v1

What's next:
    Debug this container error with Gordon → docker ai "help me fix this container error"
docker: Error response from daemon: Conflict. The container name "/app-single-stage" is already in use by container "84cc1167084b6dd56b4b1f90e654ea8ee9a589391e610d36d3bfe0e2d87c5fd8". You have to remove (or rename) that container to be able to reuse that name.

Run 'docker run --help' for more information

D:\baitap_devops\baitap\ss10\b2>docker ps -la
CONTAINER ID   IMAGE           COMMAND                  CREATED         STATUS    PORTS     NAMES
84cc1167084b   hw-backend:v1   "docker-entrypoint.s…"   3 minutes ago   Created             app-single-stage

D:\baitap_devops\baitap\ss10\b2>docker rm app-single-state
Error response from daemon: No such container: app-single-state

D:\baitap_devops\baitap\ss10\b2>docker rm app-single-stage
app-single-stage

D:\baitap_devops\baitap\ss10\b2>docker run -d --name app-single-stage -p 8080:3000 hw-backend:v1
87beb7f4c3b2345e2e31083f475902b73056c6fcdb2ffa3e0f70e1ed32a625bb

What's next:
    Debug this container error with Gordon → docker ai "help me fix this container error"
docker: Error response from daemon: ports are not available: exposing port TCP 0.0.0.0:8080 -> 127.0.0.1:0: listen tcp 0.0.0.0:8080: bind: Only one usage of each socket address (protocol/network address/port) is normally permitted.

Run 'docker run --help' for more information

D:\baitap_devops\baitap\ss10\b2>docker run -d --name app-single-stage -p 8081:3000 hw-backend:v1
7515efa7483181061095ec2cb97e52ea957fce1d2d8a14bb095e36f46e37dfa7

D:\baitap_devops\baitap\ss10\b2>docker ps
CONTAINER ID   IMAGE           COMMAND                  CREATED         STATUS         PORTS                                         NAMES
7515efa74831   hw-backend:v1   "docker-entrypoint.s…"   9 seconds ago   Up 7 seconds   0.0.0.0:8081->3000/tcp, [::]:8081->3000/tcp   app-single-stage

D:\baitap_devops\baitap\ss10\b2>curl -i http://localhost:8081/
HTTP/1.1 200 OK
X-Powered-By: Express
Content-Type: application/json; charset=utf-8
Content-Length: 64
ETag: W/"40-upZb7Fps+hszzRU9BoKtiCsmGCQ"
Date: Mon, 12 Oct 2026 20:40:36 GMT
Connection: keep-alive
Keep-Alive: timeout=5

{"status":"success","message":"Hello from Docker Single-stage!"}
D:\baitap_devops\baitap\ss10\b2>

D:\baitap_devops\baitap\ss10\b2>docker stop app-single-stage
app-single-stage