# 问题汇总

```
[root@VM_0_11_centos doclever]# systemctl start docker
Job for docker.service failed because start of the service was attempted too often. See "systemctl status docker.service" and "journalctl -xe" for details.
To force a start use "systemctl reset-failed docker.service" followed by "systemctl start docker.service" again.


对于以上这个问题，可能是 /etc/docker/daemon.json的配置错误，而我这次记录笔记是添加了镜像地址，可能导致启动不了docker
当时文件内容如下。
{
	"registry-mirrors": "可能是不可用的地址"
}
```

