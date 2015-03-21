# 一些约定

基于centos7，默认安装java7 lein wget unzip vi telnet tar which bzip2

image 有版本号

具体应用就已应用名称命名image，并且带版本号。

ENV 可以通过shell最终影响run.sh的参数，为了保证每次启动新的容器都实现同样的效果。

$ docker run --add-host=docker:10.180.0.1 --rm -it debian
$$ ping docker
PING docker (10.180.0.1): 48 data bytes
56 bytes from 10.180.0.1: icmp_seq=0 ttl=254 time=7.600 ms
56 bytes from 10.180.0.1: icmp_seq=1 ttl=254 time=30.705 ms
^C--- docker ping statistics ---
2 packets transmitted, 2 packets received, 0% packet loss
round-trip min/avg/max/stddev = 7.600/19.152/30.705/11.553 ms

$ alias hostip="ip route show 0.0.0.0/0 | grep -Eo 'via \S+' | awk '{ print \$2 }'"
$ docker run  --add-host=docker:$(hostip) --rm -it debian

http://docs.docker.com/reference/commandline/cli
