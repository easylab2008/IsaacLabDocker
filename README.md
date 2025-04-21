# 一建式启动isaacLab 2.0 + sim4.5 docker环境（支持桌面图形化）

本项目根据[isaacLab官网文档](https://isaac-sim.github.io/IsaacLab/main/index.html) 构建了完整的 isaacLab 2.0 + sim4.5 docker镜像环境（支持桌面图形化）.方便大家在自己的开发机上可一键式启动 isaacLab 2.0 + sim4.5 开发环境，无需做任何安装操作。



## 安装Docker服务（ 若已安装 可忽略）

```shell
#### 更新包索引并安装依赖
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add the repository to Apt sources:
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

#### 安装 Docker 引擎
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

```


##  安装 NVIDIA Docker 工具 （ 若已安装 可忽略）

```shell
#### 设置 NVIDIA Docker 仓库###
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list

#### 更新包索引并安装 NVIDIA Docker 工具
sudo apt-get update
sudo apt-get install -y nvidia-docker2

#### 重启 Docker 服务
sudo systemctl restart docker

```


## 验证Docker环境安装是否正常
```shell
#### 运行带有 NVIDIA 支持的测试容器 查看是否能够在容器中成功执行 nvidia-smi命令
sudo docker run -it --rm --gpus all nvidia/cuda:12.1.1-base-ubuntu20.04 nvidia-smi
```











<div align="center">

### 对本项目有任何疑问或建议，欢迎联系探讨，微信号: easylab2008

![本地图片](./images/weixin.jpg "项目架构图")

</div>
