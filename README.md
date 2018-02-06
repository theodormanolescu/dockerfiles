to run:
- docker image build -t cent7 .centos7/
- docker run -ti -d --cap-add SYS_ADMIN -v /sys/fs/cgroup:/sys/fs/cgroup -h=web --name=web1 -p 80:80 cent7