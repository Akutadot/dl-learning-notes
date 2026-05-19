# Chapter 0 前置学习记录

## 0.1 本阶段学习目标

本阶段主要完成深度学习正式学习前的基础准备，包括 Linux 开发环境搭建、Linux 基础命令学习、Conda/CUDA/cuDNN 环境了解、计算机网络基础复习、代理网络配置以及 Git/GitHub 的使用。

通过本阶段学习，希望能够具备以下能力：

1. 能够在 Windows 上使用 WSL Ubuntu 作为 Linux 开发环境；
2. 能够使用 VS Code 连接 Linux 环境进行文件编辑和代码编写；
3. 能够掌握 Linux 常用目录、文件操作命令；
4. 能够理解公网、局域网、子网划分和服务器间数据传输的基本思路；
5. 能够通过代理让 WSL Ubuntu 访问 GitHub 等外网资源；
6. 能够使用 Git 记录 Markdown 学习笔记，并上传到 GitHub。

---

# 1. Linux 基础学习

## 1.1 Linux 环境搭建

本机操作系统为 Windows，使用 WSL Ubuntu 搭建 Linux 开发环境。WSL 可以理解为 Windows 下的 Linux 子系统，可以在不单独安装实体 Linux 系统的情况下，使用 Ubuntu 终端、Linux 命令、Git、Python 环境等。

安装完成后，打开 Ubuntu 终端，可以看到类似如下提示符：

```bash
aku@Aku:~$
```

其中：

- `aku` 表示当前 Linux 用户名；
- `Aku` 表示主机名；
- `~` 表示当前位于用户主目录；
- `$` 表示当前是普通用户权限。

因此，当终端显示 `aku@Aku:~$` 时，说明已经进入 Ubuntu/Linux 环境。

本阶段还学习到，后续代码编写统一使用 VS Code，不使用 PyCharm。可以在 Ubuntu 终端中进入项目目录后，使用：

```bash
code .
```

直接用 VS Code 打开当前 Linux 文件夹。

---

## 1.2 操作系统、虚拟机与 Ubuntu 的基本理解

### 1.2.1 操作系统

操作系统是计算机硬件和应用程序之间的中间层，负责管理 CPU、内存、硬盘、文件、进程、网络等资源。常见操作系统包括 Windows、Linux、macOS 等。

平时我们直接使用的软件，例如浏览器、VS Code、Python 程序等，都需要运行在操作系统之上。

### 1.2.2 虚拟机软件

虚拟机软件可以在一台真实电脑上模拟出另一台“虚拟电脑”，并在其中安装另一个操作系统。例如，在 Windows 中通过虚拟机安装 Ubuntu。

虚拟机的优点是隔离性较好，缺点是资源占用较大。相比之下，WSL 更轻量，适合在 Windows 中快速使用 Linux 终端环境。

### 1.2.3 Ubuntu 操作系统

Ubuntu 是 Linux 的一种发行版。它基于 Linux 内核，并在内核基础上加入了系统工具、软件包管理器、桌面环境等内容，使用户能够更方便地使用 Linux。

可以理解为：

```text
Linux 内核 + 系统工具 + 软件包管理 + 用户界面 = Ubuntu 发行版
```

### 1.2.4 Linux 内核和发行版

Linux 严格来说是一个操作系统内核，负责管理硬件资源和系统底层功能。

而我们平时说的 “Linux 系统”，通常指的是基于 Linux 内核开发出来的发行版，例如：

- Ubuntu
- Debian
- CentOS
- Fedora
- Arch Linux

它们都使用 Linux 内核，但软件包管理方式、默认工具和使用习惯可能不同。

本阶段使用的是 Ubuntu，它属于 Linux 发行版。

---

## 1.3 Linux 终端命令基本格式

Linux 终端命令通常由三部分组成：

```bash
命令 [选项] [参数]
```

例如：

```bash
ls -l /home
```

其中：

- `ls` 是命令，表示查看目录内容；
- `-l` 是选项，表示以详细列表形式显示；
- `/home` 是参数，表示要查看的目录。

Linux 命令中常见两种选项写法：

### 短选项

短选项通常使用一个短横线 `-`，后面跟一个字母，例如：

```bash
ls -l
ls -a
rm -r
```

### 长选项

长选项通常使用两个短横线 `--`，后面跟完整单词，例如：

```bash
ls --help
rm --help
mkdir --help
```

短选项更简洁，长选项更容易理解。

---

## 1.4 查看命令帮助

在学习 Linux 命令时，如果忘记某个命令怎么使用，可以通过帮助命令查看。

### 1.4.1 使用 --help

例如查看 `ls` 命令的帮助：

```bash
ls --help
```

查看 `mkdir` 命令的帮助：

```bash
mkdir --help
```

`--help` 一般会显示该命令的基本功能、常用选项和使用格式。

### 1.4.2 使用 man 手册

还可以使用 `man` 命令查看更完整的帮助文档：

```bash
man ls
man rm
man cp
```

其中 `man` 是 manual 的缩写，表示查看命令手册。

进入 `man` 页面后，可以按 `q` 退出。

---

## 1.5 查看目录命令：ls

`ls` 用于查看当前目录下的文件和文件夹。

基本用法：

```bash
ls
```

常用选项包括：

```bash
ls -l
ls -a
ls -lh
```

含义如下：

| 命令 | 作用 |
|---|---|
| `ls` | 查看当前目录内容 |
| `ls -l` | 以详细列表形式显示 |
| `ls -a` | 显示所有文件，包括隐藏文件 |
| `ls -lh` | 以更容易阅读的方式显示文件大小 |

其中，以 `.` 开头的文件或文件夹是隐藏文件，例如：

```text
.bashrc
.git
```

---

## 1.6 切换目录命令：cd

`cd` 用于切换当前所在目录。

常见用法：

```bash
cd 目录名
cd ..
cd ~
cd /
```

含义如下：

| 命令 | 作用 |
|---|---|
| `cd 目录名` | 进入指定目录 |
| `cd ..` | 返回上一级目录 |
| `cd ~` | 回到当前用户主目录 |
| `cd /` | 进入根目录 |

例如：

```bash
cd ~/dl-learning-notes
```

表示进入当前用户主目录下的 `dl-learning-notes` 文件夹。

---

## 1.7 绝对路径和相对路径

Linux 中路径分为绝对路径和相对路径。

### 1.7.1 绝对路径

绝对路径从根目录 `/` 开始写。例如：

```bash
/home/aku/dl-learning-notes
```

这个路径无论当前在哪个目录，都可以准确定位到该文件夹。

### 1.7.2 相对路径

相对路径是相对于当前目录的位置。例如，如果当前已经在 `/home/aku` 目录下，可以使用：

```bash
cd dl-learning-notes
```

进入 `dl-learning-notes` 文件夹。

### 1.7.3 特殊路径符号

| 符号 | 含义 |
|---|---|
| `.` | 当前目录 |
| `..` | 上一级目录 |
| `~` | 当前用户主目录 |
| `/` | 根目录 |

例如：

```bash
cd ..
```

表示返回上一级目录。

---

## 1.8 创建文件和目录

### 1.8.1 创建文件：touch

`touch` 可以创建空文件。

例如：

```bash
touch 1.txt 2.txt
```

表示一次创建两个空文件：

```text
1.txt
2.txt
```

### 1.8.2 创建目录：mkdir

`mkdir` 用于创建文件夹。

例如：

```bash
mkdir AA BB
```

表示创建两个文件夹：

```text
AA
BB
```

如果要创建多级目录，可以使用：

```bash
mkdir -p test/a/b/c
```

其中 `-p` 表示如果中间目录不存在，就自动创建。

---

## 1.9 删除文件和目录

### 1.9.1 删除文件：rm

删除文件可以使用：

```bash
rm 文件名
```

例如：

```bash
rm 1.txt
```

### 1.9.2 删除空目录：rmdir

`rmdir` 只能删除空目录：

```bash
rmdir AA
```

如果目录中还有文件，就无法用 `rmdir` 删除。

### 1.9.3 删除目录及其内容：rm -r

如果要删除一个目录和目录中的所有内容，可以使用：

```bash
rm -r 目录名
```

例如：

```bash
rm -r AA
```

需要注意，`rm -r` 会递归删除目录，使用时要谨慎。

如果强制删除，可以使用：

```bash
rm -rf 目录名
```

但该命令风险较高，如果路径写错，可能误删重要文件，因此不建议随便使用。

---

## 1.10 拷贝、移动文件和目录

### 1.10.1 拷贝文件：cp

`cp` 用于复制文件。

例如：

```bash
cp 1.txt AA
```

表示把 `1.txt` 复制到 `AA` 文件夹中。

实际练习过程：

```bash
touch 1.txt 2.txt
mkdir AA BB
cp 1.txt AA
ls AA
```

输出：

```bash
1.txt
```

说明 `1.txt` 已经成功复制到 `AA` 目录下。

### 1.10.2 拷贝目录：cp -r

如果要复制整个文件夹，需要加 `-r`：

```bash
cp -r AA BB
```

表示把 `AA` 文件夹复制到 `BB` 中。

### 1.10.3 移动或重命名：mv

`mv` 可以用于移动文件，也可以用于重命名文件。

重命名：

```bash
mv 1.txt new.txt
```

移动文件：

```bash
mv new.txt BB
```

表示把 `new.txt` 移动到 `BB` 文件夹中。

---

## 1.11 tree 命令

学习过程中尝试使用：

```bash
tree AA
```

但终端提示：

```bash
Command 'tree' not found
```

这说明 Ubuntu 中默认没有安装 `tree` 命令。可以通过以下命令安装：

```bash
sudo apt install tree -y
```

安装完成后，可以使用：

```bash
tree AA
```

查看目录结构。

如果暂时不安装 `tree`，也可以用：

```bash
ls -R AA
```

递归查看目录内容。

---

## 1.12 Linux 基础命令学习小结

通过本阶段学习，我初步理解了 Linux 操作系统、Linux 内核与发行版之间的关系，也掌握了一些基础终端命令的使用方法。

目前已学习的内容包括：

1. 操作系统、虚拟机软件、Ubuntu 的基本概念；
2. Linux 内核与 Linux 发行版的关系；
3. Linux 终端命令的基本格式；
4. 绝对路径和相对路径；
5. `ls`、`cd`、`pwd` 等目录查看与切换命令；
6. `touch`、`mkdir` 等文件和目录创建命令；
7. `rm`、`rmdir` 等删除命令；
8. `cp`、`mv` 等复制、移动和重命名命令；
9. `--help` 和 `man` 查看命令帮助的方法；
10. `tree` 命令的作用以及安装方法。

后续还需要继续补充 Linux 权限管理、环境变量、压缩解压、进程管理、远程连接等内容。

---

# 2. Conda、CUDA、cuDNN 环境搭建

## 2.1 当前完成情况

本部分目前还未完整完成。后续需要继续学习并记录 Conda、CUDA、cuDNN 的安装和配置过程。

目前已经了解的内容如下：

- Conda 用于 Python 环境管理；
- CUDA 是 NVIDIA 提供的 GPU 并行计算平台；
- cuDNN 是 NVIDIA 针对深度学习的 GPU 加速库；
- PyTorch、TensorFlow 等深度学习框架在使用 NVIDIA GPU 训练时，通常需要 CUDA/cuDNN 支持。

## 2.2 本机硬件情况说明

本机为联想 Windows 电脑，使用 Intel 显卡，不具备 NVIDIA CUDA 环境。因此，本机无法按照常规教程配置 CUDA/cuDNN GPU 加速环境。

本地环境主要用于：

1. Linux 基础学习；
2. Python 基础学习；
3. Git 和 GitHub 使用；
4. VS Code 开发环境熟悉；
5. 小规模 CPU 代码调试。

后续如果需要进行 Transformer、VLM 等深度学习模型训练，应使用实验室服务器或云端 NVIDIA GPU 服务器完成。

## 2.3 后续计划

后续需要继续完成：

1. Miniconda 或 Anaconda 安装；
2. Conda 创建虚拟环境；
3. Conda 环境激活与退出；
4. CPU 版本 PyTorch 安装；
5. 如果有服务器，再学习 CUDA/cuDNN 版本匹配与 GPU 环境检查。

示例命令：

```bash
conda create -n dl_cpu python=3.10
conda activate dl_cpu
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
```

测试 PyTorch 是否可用：

```python
import torch

print(torch.__version__)
print(torch.cuda.is_available())
```

如果输出 `False`，说明当前没有检测到 CUDA GPU，这对于本机 Intel 显卡环境是正常情况。

---

# 3. 计算机网络基础

## 3.1 学习目标

本部分主要回顾计算机网络中的公网、局域网、IP 地址、子网划分等概念，并思考如何在两台服务器之间使用网线构建数据传输环境。

---

## 3.2 公网和局域网

### 3.2.1 公网

公网 IP 是可以在互联网中被访问的 IP 地址。例如，云服务器通常会分配公网 IP，使用户可以通过 SSH 远程连接服务器。

例如：

```text
123.xxx.xxx.xxx
```

如果服务器有公网 IP，并且安全组和防火墙允许访问，就可以在本地通过 SSH 连接：

```bash
ssh username@服务器公网IP
```

### 3.2.2 局域网

局域网 IP 是在一个小范围网络内部使用的 IP，例如家庭、宿舍、实验室、公司内部网络。

常见局域网 IP 地址段包括：

```text
192.168.x.x
10.x.x.x
172.16.x.x ~ 172.31.x.x
```

例如：

```text
192.168.1.10
192.168.1.20
```

如果两台设备在同一个局域网中，并且网络策略允许，它们可以直接通信。

---

## 3.3 IP 地址和子网掩码

IP 地址用于标识网络中的一台设备。子网掩码用于判断两个 IP 是否属于同一个网络。

例如：

```text
192.168.1.10/24
```

其中 `/24` 表示子网掩码为：

```text
255.255.255.0
```

它所在的网段是：

```text
192.168.1.0/24
```

如果两台设备分别是：

```text
192.168.1.10/24
192.168.1.20/24
```

它们属于同一网段，可以直接通信。

如果两台设备分别是：

```text
192.168.1.10/24
192.168.2.20/24
```

它们不属于同一网段，通常需要路由器进行转发。

---

## 3.4 两台服务器通过网线直连传输数据

如果有两台服务器 A 和 B，可以使用网线直接连接它们的网口，然后手动配置静态 IP，使它们处于同一网段。

例如：

```text
服务器 A：192.168.10.1/24
服务器 B：192.168.10.2/24
```

配置完成后，可以在服务器 A 上测试是否能连接服务器 B：

```bash
ping 192.168.10.2
```

如果可以 ping 通，说明两台服务器之间网络已经连通。

---

## 3.5 服务器之间传输文件

网络连通后，可以使用 `scp` 或 `rsync` 进行文件传输。

### 3.5.1 使用 scp 传输单个文件

```bash
scp test.txt user@192.168.10.2:/home/user/
```

表示把当前服务器上的 `test.txt` 复制到另一台服务器的 `/home/user/` 目录下。

### 3.5.2 使用 rsync 同步文件夹

```bash
rsync -av ./data/ user@192.168.10.2:/home/user/data/
```

`rsync` 适合传输文件夹或同步大量文件。相比 `scp`，它可以只同步变化的部分。

---

## 3.6 测试服务器之间的传输速度

如果要测试两台服务器之间的网络速度，可以使用 `iperf3`。

在服务器 B 上运行：

```bash
iperf3 -s
```

表示启动服务端。

在服务器 A 上运行：

```bash
iperf3 -c 192.168.10.2
```

表示连接服务器 B 并测试带宽。

---

## 3.7 本部分学习理解

本部分的核心理解是：

1. 公网 IP 可以被互联网访问，适合远程连接云服务器；
2. 局域网 IP 只在局域网内部使用，适合实验室或本地设备之间通信；
3. 子网掩码用于判断两台设备是否处于同一网段；
4. 两台服务器如果用网线直连，需要手动配置同一网段的静态 IP；
5. 服务器之间传输数据前，首先要保证网络连通；
6. 网络连通后，可以使用 `scp`、`rsync` 等工具传输数据。

---

# 4. 科学上网与 WSL 代理配置

## 4.1 当前完成情况

本机已经具备访问外网的能力，Windows 浏览器可以正常访问 GitHub。随后进一步完成了 WSL Ubuntu 通过 Windows 代理访问 GitHub，并成功使用 Git 将本地 Markdown 学习记录推送到 GitHub。

虽然任务中提到 Clash Verge，但本机实际检测到的代理进程并不是 Clash Verge，而是：

```text
com.vortex.helper.exe
```

其功能上同样提供了本机代理服务。

---

## 4.2 检查 Windows 代理端口

在 Windows PowerShell 中输入：

```powershell
netstat -ano | findstr :7897
```

输出中可以看到：

```powershell
TCP    0.0.0.0:7897    0.0.0.0:0    LISTENING    2792
```

这说明 Windows 上的 `7897` 端口处于监听状态。

继续使用：

```powershell
tasklist | findstr 2792
```

输出为：

```powershell
com.vortex.helper.exe
```

说明该代理端口由 `com.vortex.helper.exe` 进程提供。

---

## 4.3 WSL 不能直接使用 localhost 的原因

启动 WSL 时，终端提示：

```text
wsl: 检测到 localhost 代理配置，但未镜像到 WSL。NAT 模式下的 WSL 不支持 localhost 代理。
```

这说明 WSL Ubuntu 不能直接使用 Windows 的 `localhost` 代理。

也就是说，在 Windows 中可以使用：

```text
127.0.0.1:7897
```

但在 WSL Ubuntu 中，不能简单地使用 `127.0.0.1:7897` 访问 Windows 代理。需要先获取 WSL 访问 Windows 主机的网关 IP。

---

## 4.4 获取 WSL 访问 Windows 的网关 IP

在 Ubuntu 终端中输入：

```bash
hostip=$(ip route | awk '/default/ {print $3}')
echo $hostip
```

本机输出为：

```bash
172.20.64.1
```

因此，WSL 中访问 Windows 代理时，应使用：

```text
172.20.64.1:7897
```

---

## 4.5 测试 WSL 是否可以通过代理访问 GitHub

在 Ubuntu 终端中输入：

```bash
curl -I -x http://$hostip:7897 https://github.com -m 10
```

测试返回：

```text
HTTP/1.1 200 Connection established
HTTP/2 200
```

这说明 WSL Ubuntu 已经可以通过 Windows 代理访问 GitHub。

---

## 4.6 配置 WSL 临时代理

每次新开 Ubuntu 终端后，如果需要访问 GitHub，可以先输入：

```bash
hostip=$(ip route | awk '/default/ {print $3}')
export http_proxy=http://$hostip:7897
export https_proxy=http://$hostip:7897
```

这两条 `export` 命令只是临时配置代理，只对当前终端窗口有效。关闭终端后，下次需要重新设置。

---

## 4.7 本部分学习理解

本部分的核心理解是：

1. Windows 可以通过代理软件访问外网；
2. WSL Ubuntu 与 Windows 不是完全相同的网络环境；
3. WSL 中不能直接使用 Windows 的 `localhost` 代理；
4. 需要通过 WSL 的默认网关 IP 访问 Windows 主机代理端口；
5. 本机可用代理端口为 `7897`；
6. 配置代理后，WSL 可以正常访问 GitHub 并完成 `git push`。

---

# 5. Git 使用与 GitHub 上传

## 5.1 Git 安装

在 Ubuntu 中使用以下命令安装 Git：

```bash
sudo apt update
sudo apt install git -y
```

安装完成后检查版本：

```bash
git --version
```

本机输出：

```bash
git version 2.53.0
```

说明 Git 安装成功。

---

## 5.2 Git 用户信息配置

首次使用 Git 时，需要配置用户名和邮箱：

```bash
git config --global user.name "Aku"
git config --global user.email "自己的邮箱"
```

检查配置：

```bash
git config --global --list
```

如果输出中包含：

```bash
user.name=Aku
user.email=自己的邮箱
```

说明配置成功。

---

## 5.3 创建学习记录文件夹

在 Ubuntu 终端中创建学习记录文件夹：

```bash
mkdir dl-learning-notes
cd dl-learning-notes
touch README.md
```

然后使用 VS Code 打开：

```bash
code .
```

在 VS Code 中编辑 `README.md` 文件，用于记录本阶段学习内容。

---

## 5.4 初始化 Git 仓库

在 `dl-learning-notes` 文件夹中执行：

```bash
git init
```

该命令会将当前文件夹初始化为 Git 仓库。

然后将文件加入暂存区：

```bash
git add .
```

提交第一次版本：

```bash
git commit -m "Initial learning notes"
```

其中：

- `git init`：初始化本地仓库；
- `git add .`：添加当前目录下所有修改；
- `git commit`：生成一次本地版本记录；
- `-m`：添加提交说明。

---

## 5.5 创建 GitHub 远程仓库

在 GitHub 官网中新建仓库，仓库名为：

```text
dl-learning-notes
```

创建时没有勾选 `Add a README file`，因为本地已经有 `README.md`。

创建完成后，在 Ubuntu 终端中添加远程仓库：

```bash
git remote add origin https://github.com/Akutadot/dl-learning-notes.git
```

将分支改名为 `main`：

```bash
git branch -M main
```

推送到 GitHub：

```bash
git push -u origin main
```

推送成功后，GitHub 网页中可以看到 `README.md` 文件。

---

## 5.6 GitHub Token 认证

第一次推送时，GitHub 不再支持直接输入账号密码。因此，如果终端提示输入密码，不能输入 GitHub 登录密码，而需要使用 GitHub Personal Access Token。

GitHub Token 的生成位置：

```text
GitHub 头像
Settings
Developer settings
Personal access tokens
Tokens classic
Generate new token
```

生成时需要勾选 `repo` 权限。

终端提示：

```text
Username for 'https://github.com':
```

输入 GitHub 用户名：

```text
Akutadot
```

终端提示：

```text
Password for 'https://Akutadot@github.com':
```

此处粘贴 GitHub Token。粘贴时终端不会显示字符，这是正常现象，粘贴后直接回车即可。

注意：Token 不能写入 README，也不能上传到 GitHub。

---

## 5.7 后续每次更新 README.md 的流程

以后每次在 VS Code 中修改 `README.md` 后，不会自动同步到 GitHub，需要手动执行 Git 命令。

完整流程如下。

### 第一步：进入学习记录文件夹

```bash
cd ~/dl-learning-notes
```

### 第二步：用 VS Code 打开

```bash
code .
```

在 VS Code 中修改 `README.md`，修改完成后按：

```text
Ctrl + S
```

保存文件。

### 第三步：配置 WSL 代理

因为 WSL 不能自动使用 Windows 的 localhost 代理，所以新开 Ubuntu 终端后，需要先配置代理：

```bash
hostip=$(ip route | awk '/default/ {print $3}')
export http_proxy=http://$hostip:7897
export https_proxy=http://$hostip:7897
```

### 第四步：查看 Git 状态

```bash
git status
```

如果修改了 README.md，会看到类似：

```text
modified: README.md
```

### 第五步：添加修改

```bash
git add .
```

### 第六步：提交修改

```bash
git commit -m "Update learning notes"
```

### 第七步：推送到 GitHub

```bash
git push
```

推送成功后，刷新 GitHub 仓库网页，即可看到最新的 Markdown 内容。

---

## 5.8 如果出现 nothing to commit

如果输入：

```bash
git commit -m "Update learning notes"
```

后提示：

```text
nothing to commit, working tree clean
```

说明当前没有新的修改。可能原因包括：

1. VS Code 中修改后没有按 `Ctrl + S` 保存；
2. 文件内容实际上没有变化；
3. 当前终端不在 `dl-learning-notes` 文件夹中。

可以先检查当前目录：

```bash
pwd
```

如果不是：

```bash
/home/aku/dl-learning-notes
```

则需要先进入：

```bash
cd ~/dl-learning-notes
```

---

## 5.9 本部分学习理解

本部分的核心理解是：

1. VS Code 只是编辑器，不会自动上传 GitHub；
2. Git 负责记录本地文件修改；
3. GitHub 是远程代码仓库；
4. 修改文件后必须经过 `git add`、`git commit`、`git push` 三步，网页才会更新；
5. WSL 中推送 GitHub 需要配置代理；
6. GitHub HTTPS 推送需要使用 Token，而不是登录密码。

---

# 6. Chapter 0 当前完成情况总结

| 项目 | 当前状态 | 说明 |
|---|---|---|
| Linux 环境搭建 | 已完成 | 已安装 WSL Ubuntu，并能使用 Ubuntu 终端 |
| VS Code 连接 Linux | 已完成 | 可通过 `code .` 打开 Linux 文件夹 |
| Linux 基础指令学习 | 进行中 | 已学习目录、路径、文件创建、删除、复制、移动等基础命令，后续继续补充 |
| Conda 环境搭建 | 未完成 | 后续继续安装和记录 |
| CUDA/cuDNN | 本机不适合配置 | 本机为 Intel 显卡，不支持 NVIDIA CUDA |
| 计算机网络 | 已整理基础知识 | 已理解公网、局域网、子网划分、服务器直连传输思路 |
| 科学上网 | 已完成本机与 WSL 代理配置 | WSL 可通过 7897 端口访问 GitHub |
| Git 使用 | 已完成基础流程 | 已能创建本地仓库并推送到 GitHub |
| Markdown 上传 GitHub | 已完成 | 已将 README.md 上传至 GitHub 仓库 |

---

# 7. 后续学习计划

1. 继续完成 Linux 基础指令学习，补充权限、压缩解压、进程管理、环境变量等内容；
2. 安装并学习 Conda，掌握虚拟环境创建、激活、删除和依赖管理；
3. 在本地 CPU 环境下测试 Python 和 PyTorch 基础代码；
4. 后续如果获得 GPU 服务器账号，学习 SSH 连接服务器、检查 GPU 状态和配置深度学习环境；
5. 持续使用 Markdown 记录学习过程，并通过 Git 上传到 GitHub。
