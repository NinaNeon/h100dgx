```bash
USER@DESKTOP-QF7UBMR MINGW64 /
$ ssh -i ~/.ssh/id_ed25519 -p 2222 \
-o "ProxyCommand=ssh -i ~/.ssh/id_ed25519 -W %h:%p -p 2222 caijingnina-gmai-11e66a@jb1.frontier.nvidia.com" \
caijingnina-gmai-11e66a@3.tun.tp1-cluster.nvidia.com
The authenticity of host '[3.tun.tp1-cluster.nvidia.com]:2222 (<no hostip for proxy command>)' can't be established.
ED25519 key fingerprint is SHA256:iWkGhdL/1nLrFwLgyguxVH07Ebiqx3lSF7zfXvsl7Tk.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[3.tun.tp1-cluster.nvidia.com]:2222' (ED25519) to the list of known hosts.
Creating ECDSA key for ssh
caijingnina-gmai-11e66a@TRDC01:~$ ^C
caijingnina-gmai-11e66a@TRDC01:~$ hostname
TRDC01
caijingnina-gmai-11e66a@TRDC01:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute
       valid_lft forever preferred_lft forever
2: eno8303: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether c4:cb:e1:a0:cd:24 brd ff:ff:ff:ff:ff:ff
    altname enp4s0f0
3: eno8403: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether c4:cb:e1:a0:cd:25 brd ff:ff:ff:ff:ff:ff
    altname enp4s0f1
4: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9000 qdisc mq state UP group default qlen 1000
    link/ether 94:6d:ae:c8:2e:96 brd ff:ff:ff:ff:ff:ff
    altname enp23s0np0
    inet 10.225.1.130/27 brd 10.225.1.159 scope global dynamic eth0
       valid_lft 604335sec preferred_lft 604335sec
    inet6 fe80::966d:aeff:fec8:2e96/64 scope link
       valid_lft forever preferred_lft forever
caijingnina-gmai-11e66a@TRDC01:~$ nvidia-smi
Command 'nvidia-smi' not found, but can be installed with:
apt install nvidia-utils-470         # version 470.256.02-0ubuntu0.24.04.1, or
apt install nvidia-utils-470-server  # version 470.256.02-0ubuntu0.24.04.1
apt install nvidia-utils-535         # version 535.274.02-0ubuntu0.24.04.2
apt install nvidia-utils-535-server  # version 535.274.02-0ubuntu0.24.04.2
apt install nvidia-utils-570         # version 570.195.03-0ubuntu0.24.04.1
apt install nvidia-utils-570-server  # version 570.195.03-0ubuntu0.24.04.2
apt install nvidia-utils-580         # version 580.95.05-0ubuntu0.24.04.2
apt install nvidia-utils-580-server  # version 580.95.05-0ubuntu0.24.04.2
apt install nvidia-utils-565-server  # version 565.57.01-0ubuntu0.24.04.3
apt install nvidia-utils-525         # version 525.147.05-0ubuntu1
apt install nvidia-utils-525-server  # version 525.147.05-0ubuntu1
apt install nvidia-utils-550-server  # version 550.163.01-0ubuntu0.24.04.1
Ask your administrator to install one of them.
caijingnina-gmai-11e66a@TRDC01:~$
```

你在唬爛我 我進去了:
```bash
USER@DESKTOP-QF7UBMR MINGW64 / $ ssh -i ~/.ssh/id_ed25519 -p 2222 \ -o "ProxyCommand=ssh -i ~/.ssh/id_ed25519 -W %h:%p -p 2222 caijingnina-gmai-11e66a@jb1.frontier.nvidia.com" \ caijingnina-gmai-11e66a@3.tun.tp1-cluster.nvidia.com The authenticity of host '[3.tun.tp1-cluster.nvidia.com]:2222 (<no hostip for proxy command>)' can't be established. ED25519 key fingerprint is SHA256:iWkGhdL/1nLrFwLgyguxVH07Ebiqx3lSF7zfXvsl7Tk. This key is not known by any other names. Are you sure you want to continue connecting (yes/no/[fingerprint])? yes Warning: Permanently added '[3.tun.tp1-cluster.nvidia.com]:2222' (ED25519) to the list of known hosts. Creating ECDSA key for ssh caijingnina-gmai-11e66a@TRDC01:~$ 
```

你的成功命令是：

```bash
ssh -i ~/.ssh/id_ed25519 -p 2222 \
-o "ProxyCommand=ssh -i ~/.ssh/id_ed25519 -W %h:%p -p 2222 caijingnina-gmai-11e66a@jb1.frontier.nvidia.com" \
caijingnina-gmai-11e66a@3.tun.tp1-cluster.nvidia.com
```


```bash
hostname
```

确认机器名（例如 `TRDC01` 你已经看到）

然后跑：

```bash
ip addr
```

或

```bash
nvidia-smi
```

```bash
USER@DESKTOP-QF7UBMR MINGW64 /
$ ssh -i ~/.ssh/id_ed25519 -p 2222 \
-o "ProxyCommand=ssh -i ~/.ssh/id_ed25519 -W %h:%p -p 2222 caijingnina-gmai-11e66a@jb1.frontier.nvidia.com" \
caijingnina-gmai-11e66a@3.tun.tp1-cluster.nvidia.com
Last login: Tue Dec 23 15:11:29 2025 from 127.0.0.1
caijingnina-gmai-11e66a@TRDC01:~$ module load slurm
sinfo
PARTITION AVAIL  TIMELIMIT  NODES  STATE NODELIST
p01          up   infinite      4  down* cnode3-[001-004]
p01          up   infinite      1  alloc cnode3-005
caijingnina-gmai-11e66a@TRDC01:~$ srun -N 1 -p NTU_Shared --gres=gpu:1 --pty /bin/bash
srun: error: invalid partition specified: NTU_Shared
srun: error: Unable to allocate resources: Invalid partition name specified
caijingnina-gmai-11e66a@TRDC01:~$ ^C
caijingnina-gmai-11e66a@TRDC01:~$ srun -N 1 -p p01 --gres=gpu:1 --pty /bin/bash
srun: job 156 queued and waiting for resources

caijingnina-gmai-11e66a@TRDC01:~$ srun -N 1 -p p01 --gres=gpu:1 --pty /bin/bash
srun: job 156 queued and waiting for resources
^Csrun: Force Terminated JobId=156
srun: Job allocation 156 has been revoked
caijingnina-gmai-11e66a@TRDC01:~$ nvidia-smi
Command 'nvidia-smi' not found, but can be installed with:
apt install nvidia-utils-470         # version 470.256.02-0ubuntu0.24.04.1, or
apt install nvidia-utils-470-server  # version 470.256.02-0ubuntu0.24.04.1
apt install nvidia-utils-535         # version 535.274.02-0ubuntu0.24.04.2
apt install nvidia-utils-535-server  # version 535.274.02-0ubuntu0.24.04.2
apt install nvidia-utils-570         # version 570.195.03-0ubuntu0.24.04.1
apt install nvidia-utils-570-server  # version 570.195.03-0ubuntu0.24.04.2
apt install nvidia-utils-580         # version 580.95.05-0ubuntu0.24.04.2
apt install nvidia-utils-580-server  # version 580.95.05-0ubuntu0.24.04.2
apt install nvidia-utils-565-server  # version 565.57.01-0ubuntu0.24.04.3
apt install nvidia-utils-525         # version 525.147.05-0ubuntu1
apt install nvidia-utils-525-server  # version 525.147.05-0ubuntu1
apt install nvidia-utils-550-server  # version 550.163.01-0ubuntu0.24.04.1
Ask your administrator to install one of them.
caijingnina-gmai-11e66a@TRDC01:~$

```





