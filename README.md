# 深度学习笔记
## Chapter 0 前置学习
## 一、学习目标

本阶段主要完成深度学习正式学习前的环境准备和基础知识学习，包括 Linux 开发环境搭建、Git 与 GitHub 使用、Conda 环境管理、CUDA/cuDNN 环境了解、计算机网络基础回顾，以及代理网络配置。通过本阶段学习，为后续深度学习基础、经典论文复现和 VLM 模型构建打下基础。

---

## 二、Linux 基础学习

### 2.1 Linux 环境搭建

本机操作系统为 Windows，采用 WSL Ubuntu 的方式搭建 Linux 开发环境。WSL 可以在 Windows 系统中运行 Linux 终端，适合进行深度学习代码开发、Git 使用、Python 环境管理和远程服务器连接等操作。

安装完成后，打开 Ubuntu 终端，可以看到类似如下命令行提示符：

```bash
aku@Aku:~$
```

这说明当前已经进入 Ubuntu/Linux 终端环境。

### 2.2 系统更新

在 Linux 环境中，首先使用以下命令更新软件源：

```bash
sudo apt update
```

该命令用于从 Ubuntu 软件源获取最新的软件包信息。执行过程中系统会连接 Ubuntu 官方源，并下载软件包索引。

### 2.3 Git 安装检查

使用以下命令安装 Git：

```bash
sudo apt install git -y
```

安装完成后，使用以下命令检查 Git 是否安装成功：

```bash
git --version
```

本机输出结果为：

```bash
git version 2.53.0
```

说明 Git 已在 WSL Ubuntu 环境中成功安装。

### 2.4 常用 Linux 命令记录

在 Linux 学习过程中，记录了以下常用命令：

| 命令 | 作用 |
|---|---|
| `pwd` | 查看当前所在目录 |
| `ls` | 查看当前目录下的文件和文件夹 |
| `cd` | 切换目录 |
| `mkdir` | 创建文件夹 |
| `touch` | 创建空文件 |
| `cat` | 查看文件内容 |
| `cp` | 复制文件或文件夹 |
| `mv` | 移动文件或重命名文件 |
| `rm` | 删除文件 |
| `chmod` | 修改文件权限 |
| `sudo` | 以管理员权限执行命令 |

示例命令如下：

```bash
pwd
ls
mkdir test_folder
cd test_folder
touch note.txt
cat note.txt
cd ..
rm -r test_folder
```

通过这些命令，可以完成 Linux 中基础的文件和目录管理操作。

---

## 三、VS Code 连接 WSL Ubuntu

### 3.1 使用 VS Code 打开 Linux 文件夹

课程要求后续代码编写统一使用 VS Code，不使用 PyCharm。因此，本阶段尝试在 WSL Ubuntu 中使用 VS Code 打开项目文件夹。

首先创建学习记录文件夹：

```bash
mkdir dl-learning-notes
cd dl-learning-notes
touch README.md
```

然后使用以下命令打开 VS Code：

```bash
code .
```

执行后，VS Code 会打开当前 Linux 文件夹：

```bash
/home/aku/dl-learning-notes
```

在 VS Code 左侧资源管理器中可以看到 `README.md` 文件，说明 VS Code 已经成功连接 WSL Ubuntu 环境。

### 3.2 Markdown 文件记录

本阶段使用 Markdown 文件记录学习过程。Markdown 文件后缀为 `.md`，常用于项目说明、学习笔记和技术文档。

例如，本项目中使用：

```bash
README.md
```

作为主要学习记录文件。GitHub 会自动识别并展示 `README.md` 内容，因此适合作为学习报告入口。

---

## 四、Git 与 GitHub 使用

### 4.1 Git 用户信息配置

首次使用 Git 前，需要配置用户名和邮箱，用于记录每次提交的作者信息。

配置命令如下：

```bash
git config --global user.name "Aku"
git config --global user.email "自己的邮箱"
```

检查配置是否成功：

```bash
git config --global --list
```

输出中若出现：

```bash
user.name=Aku
user.email=自己的邮箱
```

说明配置成功。

### 4.2 初始化本地 Git 仓库

在 `dl-learning-notes` 文件夹中执行：

```bash
git init
```

该命令会将当前文件夹初始化为 Git 仓库，生成隐藏的 `.git` 文件夹，用于记录版本信息。

### 4.3 添加文件并提交

将当前文件夹中的文件加入 Git 暂存区：

```bash
git add .
```

提交当前版本：

```bash
git commit -m "Initial learning notes"
```

其中：

- `git add .` 表示添加当前目录下所有修改；
- `git commit` 表示生成一次本地版本记录；
- `-m` 后面的内容是本次提交说明。

执行成功后，本地 Git 仓库中已经记录了当前版本。

### 4.4 连接 GitHub 远程仓库

在 GitHub 官网新建仓库，仓库名称为：

```text
dl-learning-notes
```

创建仓库时没有勾选 `Add a README file`，因为本地已经创建了 `README.md` 文件。

随后在 Ubuntu 终端中添加远程仓库地址：

```bash
git remote add origin https://github.com/Akutadot/dl-learning-notes.git
```

将当前分支重命名为 `main`：

```bash
git branch -M main
```

推送到 GitHub：

```bash
git push -u origin main
```

推送成功后，GitHub 仓库页面可以看到本地上传的 `README.md` 文件。

### 4.5 后续更新流程

以后每次修改学习记录后，需要手动上传到 GitHub。流程如下：

```bash
git add .
git commit -m "Update learning notes"
git push
```

需要注意的是，VS Code 中保存文件并不会自动上传到 GitHub。必须执行 `git push` 后，GitHub 页面才会更新。

---

## 五、Conda、CUDA、cuDNN 环境学习

### 5.1 Conda 环境说明

Conda 是常用的 Python 环境管理工具，可以为不同项目创建独立环境，避免不同项目之间的依赖冲突。后续深度学习项目通常会使用 Conda 创建独立环境，例如：

```bash
conda create -n dl_cpu python=3.10
conda activate dl_cpu
```

其中：

- `conda create` 用于创建新环境；
- `-n dl_cpu` 表示环境名称为 `dl_cpu`；
- `python=3.10` 表示指定 Python 版本；
- `conda activate` 用于进入该环境。

### 5.2 CUDA 与 cuDNN 说明

CUDA 是 NVIDIA 提供的 GPU 并行计算平台，cuDNN 是 NVIDIA 针对深度学习计算提供的加速库。通常在使用 PyTorch、TensorFlow 等深度学习框架进行 GPU 训练时，需要配置 CUDA 和 cuDNN。

但本机显卡为 Intel 显卡，不属于 NVIDIA CUDA 支持范围，因此无法在本地配置 CUDA/cuDNN GPU 加速环境。

本机环境主要用于：

- Linux 基础学习；
- Python 编程学习；
- Git 与 GitHub 使用；
- 小规模深度学习代码调试；
- CPU 版本 PyTorch 测试。

后续如果需要训练 Transformer、VLM 等计算量较大的模型，将使用实验室服务器或云端 NVIDIA GPU 服务器完成。

### 5.3 CPU 版 PyTorch 环境思路

如果后续需要在本机测试 PyTorch，可以安装 CPU 版本：

```bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
```

测试代码：

```python
import torch

print(torch.__version__)
print(torch.cuda.is_available())
```

如果输出：

```python
False
```

说明当前 PyTorch 没有检测到 CUDA GPU，这是符合本机 Intel 显卡环境的正常情况。

---

## 六、计算机网络基础学习

### 6.1 公网与局域网

公网 IP 是可以在互联网中被访问的 IP 地址，通常用于云服务器、网站服务器等场景。局域网 IP 是在同一局域网内部使用的地址，常见于家庭、宿舍、实验室或公司内部网络。

常见的局域网 IP 地址段包括：

```text
192.168.x.x
10.x.x.x
172.16.x.x ~ 172.31.x.x
```

例如，家用路由器下的电脑 IP 可能是：

```text
192.168.1.10
```

另一台设备可能是：

```text
192.168.1.20
```

如果它们处于同一个网段，通常可以直接通信。

### 6.2 子网划分

子网划分用于判断两个 IP 地址是否属于同一网络。常见写法为：

```text
192.168.1.10/24
```

其中 `/24` 表示子网掩码为：

```text
255.255.255.0
```

这说明该主机位于：

```text
192.168.1.0/24
```

这个网段中。

如果两台设备分别为：

```text
192.168.1.10/24
192.168.1.20/24
```

它们属于同一个局域网网段，可以直接通信。

如果两台设备分别为：

```text
192.168.1.10/24
192.168.2.20/24
```

它们不在同一个网段，通常需要通过路由器进行转发。

### 6.3 两台服务器之间使用网线传输数据

如果有两台服务器 A 和 B，可以通过网线直连，并手动设置静态 IP，使它们处于同一网段。

例如：

```text
服务器 A：192.168.10.1/24
服务器 B：192.168.10.2/24
```

配置完成后，可以在服务器 A 上测试是否能连接服务器 B：

```bash
ping 192.168.10.2
```

如果可以 ping 通，说明两台服务器之间网络连通。

之后可以使用 `scp` 传输文件：

```bash
scp test.txt user@192.168.10.2:/home/user/
```

也可以使用 `rsync` 同步文件夹：

```bash
rsync -av ./data/ user@192.168.10.2:/home/user/data/
```

如果需要测试两台服务器之间的网络传输速度，可以使用 `iperf3`。

在服务器 B 上运行：

```bash
iperf3 -s
```

在服务器 A 上运行：

```bash
iperf3 -c 192.168.10.2
```

这样可以测试两台服务器之间的实际带宽和传输性能。

### 6.4 本阶段理解

通过本阶段学习，我理解了公网、局域网、IP 地址、子网掩码和同网段通信的基本概念。对于服务器之间的数据传输，核心是先保证网络连通，再使用 `scp`、`rsync` 等工具进行文件传输。

---

## 七、科学上网与 WSL 代理配置

### 7.1 本机代理情况

本机 Windows 系统已经具备访问外网的能力，可以正常访问 GitHub 等网站。经检查，Windows 端代理服务运行在 `7897` 端口。

在 Windows PowerShell 中使用以下命令检查端口占用情况：

```powershell
netstat -ano | findstr :7897
```

输出结果显示：

```powershell
TCP    0.0.0.0:7897    0.0.0.0:0    LISTENING    2792
```

说明 `7897` 端口处于监听状态。随后使用以下命令查看对应进程：

```powershell
tasklist | findstr 2792
```

结果显示：

```powershell
com.vortex.helper.exe
```

说明本机代理服务由 `com.vortex.helper.exe` 进程提供。

### 7.2 WSL 不能直接使用 localhost 的原因

WSL Ubuntu 虽然运行在 Windows 上，但它和 Windows 的网络环境并不完全相同。因此，在 WSL 中不能简单地使用：

```text
127.0.0.1:7897
```

或：

```text
localhost:7897
```

来访问 Windows 代理。需要先获取 WSL 访问 Windows 主机的网关 IP。

### 7.3 获取 WSL 网关 IP

在 Ubuntu 终端中输入：

```bash
hostip=$(ip route | awk '/default/ {print $3}')
echo $hostip
```

本机输出结果为：

```bash
172.20.64.1
```

因此，WSL 中访问 Windows 代理时，应使用：

```text
172.20.64.1:7897
```

### 7.4 测试 WSL 是否可以通过代理访问 GitHub

在 Ubuntu 终端中使用以下命令测试：

```bash
curl -I -x http://$hostip:7897 https://github.com -m 10
```

测试结果返回：

```bash
HTTP/1.1 200 Connection established
HTTP/2 200
```

说明 WSL Ubuntu 已经可以通过 Windows 端代理访问 GitHub。

### 7.5 配置 WSL 临时代理

在 Ubuntu 终端中输入：

```bash
export http_proxy=http://$hostip:7897
export https_proxy=http://$hostip:7897
```

配置后，当前终端会话中的命令可以通过代理访问外网。例如，Git 可以使用该代理推送代码到 GitHub。

### 7.6 GitHub 推送验证

配置代理后，执行：

```bash
git push -u origin main
```

推送成功后，终端显示：

```bash
To https://github.com/Akutadot/dl-learning-notes.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```

说明 WSL 中的 Git 已成功通过代理连接 GitHub，并将本地 Markdown 学习记录上传至远程仓库。

---

## 八、目前完成情况总结

| 学习内容 | 完成情况 |
|---|---|
| Linux 环境搭建 | 已完成，使用 WSL Ubuntu |
| VS Code 连接 Linux 环境 | 已完成，可通过 `code .` 打开项目 |
| Git 安装 | 已完成，版本为 2.53.0 |
| Git 用户配置 | 已完成 |
| Markdown 学习记录 | 已创建 README.md |
| GitHub 仓库创建 | 已完成 |
| 本地仓库推送到 GitHub | 已完成 |
| Conda / CUDA / cuDNN | 已了解基本概念，本机因 Intel 显卡不配置 CUDA |
| 计算机网络基础 | 已学习公网、局域网、子网划分和服务器直连思路 |
| 科学上网与 WSL 代理 | 已完成，WSL 可通过 7897 端口访问 GitHub |

---

## 九、后续计划

1. 继续补充 Linux 基础命令使用记录；
2. 学习 Conda 环境创建、激活、删除和依赖管理；
3. 在 CPU 环境下测试 Python 与 PyTorch 基础代码；
4. 继续学习 Git 分支、远程仓库、版本回退等操作；
5. 后续如获得 GPU 服务器账号，将学习 SSH 远程连接、服务器 Conda 环境配置以及 GPU 训练环境检查方法。

---

## 十、常用命令汇总

### 打开学习记录文件夹

```bash
cd ~/dl-learning-notes
code .
```

### 每次更新后上传 GitHub

如果当前终端已经可以访问 GitHub，直接执行：

```bash
git add .
git commit -m "Update learning notes"
git push
```

如果新开终端后无法访问 GitHub，需要先配置代理：

```bash
hostip=$(ip route | awk '/default/ {print $3}')
export http_proxy=http://$hostip:7897
export https_proxy=http://$hostip:7897
```

然后再执行：

```bash
git add .
git commit -m "Update learning notes"
git push
```