# Docker-CUDA-Caffe-install

- [reference 1](https://blog.csdn.net/qq_41493990/article/details/81624419)
- [reference 2](https://blog.csdn.net/junxiacaocao/article/details/79471770)
- [reference 3](https://zhuanlan.zhihu.com/p/28916121)
- [reference 4](https://blog.csdn.net/u011987514/article/details/70943378)
---

## (1). Installer docker
```C++
$ sudo apt-get remove docker docker-engine docker.io
$ sudo apt-get update
$ sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
$ sudo apt-key fingerprint 0EBFCD88 
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
$ sudo apt-get update
```

```C++
$ sudo apt-get install -y docker-ce
$ sudo apt-get install docker-ce     ###开始安装docker 
$ apt-cache madison docker-ce        ###加载docker 
$ sudo docker run hello-world
```

### Test whether install successfully or not 
```C++
docker info 
```

### Delete docker
```C++
$ sudo apt-get purge docker-ce
$ sudo rm -rf /var/lib/docker
```

### show docker images
```C++
$ docker images
```

## (2). Install nvidia-docker and nvidia-docker-plugin
```C++
$ wget -P /tmp https://github.com/NVIDIA/nvidia-docker/releases/download/v1.0.1/nvidia-docker_1.0.1-1_amd64.deb  
$ sudo dpkg -i /tmp/nvidia-docker*.deb && rm /tmp/nvidia-docker*.deb
```

```C++
$ sudo service nvidia-docker start
$ sudo nvidia-docker-plugin
```

## (3). Install docker CUDA
```C++
$ nvidia-docker pull nvidia/cuda:9.0-runtime-ubuntu16.04
```
```C++
$ nvidia-docker run --rm nvidia/cuda:9.0-runtime-ubuntu16.04 nvidia-smi
```
than you can see the result as same as "$ nvidia-smi" <br/>


## (4). Install docker Caffe
```C++
$ nvidia-docker run -ti bvlc/caffe:gpu caffe --version 
```


