# Chapter 0 前置学习记录

## 0.1 本阶段学习目标

本阶段主要完成深度学习正式学习前的基础准备，包括 Linux 开发环境搭建、Linux 基础命令学习、Conda/CUDA/cuDNN 环境了解、计算机网络基础复习、代理网络配置、Git/GitHub 的使用，以及云端 GPU 环境的初步使用。

通过本阶段学习，希望能够具备以下能力：

1. 能够在 Windows 上使用 WSL Ubuntu 作为 Linux 开发环境；
2. 能够使用 VS Code 连接 Linux 环境进行文件编辑和代码编写；
3. 能够掌握 Linux 常用目录、文件操作命令；
4. 能够理解公网、局域网、子网划分和服务器间数据传输的基本思路；
5. 能够通过代理让 WSL Ubuntu 访问 GitHub 等外网资源；
6. 能够使用 Git 记录 Markdown 学习笔记，并上传到 GitHub；
7. 能够理解本机 CPU/核显与 NVIDIA GPU 的区别；
8. 能够使用 AutoDL 云端 GPU 实例运行 PyTorch CUDA 代码。

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

## 1.2 操作系统

操作系统是连接计算机硬件和应用软件之间的系统软件。用户平时使用的浏览器、VS Code、Python 程序等应用软件，不能直接控制硬件，而是通过操作系统来间接使用 CPU、内存、硬盘、网络等资源。

可以简单理解为：

```text
用户 / 应用软件
        ↓
操作系统
        ↓
计算机硬件
```

常见操作系统包括：

- Windows
- macOS
- Linux
- iOS
- Android

操作系统的主要作用包括：

1. 管理硬件资源，例如 CPU、内存、硬盘、显卡、网络设备等；
2. 管理文件和目录；
3. 管理进程和程序运行；
4. 提供用户与计算机交互的界面；
5. 为应用软件提供运行环境。

本阶段学习 Linux，主要是为了熟悉深度学习开发中常用的服务器环境。后续连接实验室服务器、云端 GPU、配置 Python/Conda/PyTorch 环境时，大部分操作都需要在 Linux 命令行中完成。

---

## 1.3 虚拟机软件

虚拟机软件可以在一台真实电脑中模拟出另一台“虚拟电脑”，并在虚拟电脑中安装其他操作系统。例如，在 Windows 电脑中通过 VMware、VirtualBox 等软件安装 Ubuntu。

虚拟机的基本结构可以理解为：

```text
真实电脑
  └── Windows / macOS
        └── 虚拟机软件
              └── 虚拟机
                    └── Ubuntu 操作系统
```

虚拟机的优点：

1. 可以在不改变原系统的情况下学习 Linux；
2. 虚拟机环境相对独立，不容易影响主系统；
3. 适合练习系统安装、Linux 命令、网络配置等内容。

虚拟机的缺点：

1. 占用较多 CPU、内存和硬盘资源；
2. 图形界面和文件读写速度可能比真实系统慢；
3. 对初学者来说，网络配置和共享文件夹配置有时较复杂。

本机目前使用的是 WSL Ubuntu，不是传统虚拟机。WSL 比虚拟机更轻量，适合在 Windows 中快速使用 Linux 终端环境。

---

## 1.4 Ubuntu 操作系统

Ubuntu 是一种基于 Linux 内核的操作系统发行版。它在 Linux 内核基础上加入了系统工具、软件包管理器、图形界面和常用软件，使用户可以更方便地使用 Linux。

可以理解为：

```text
Linux 内核 + 系统工具 + 软件包管理器 + 用户界面 = Ubuntu
```

Ubuntu 常用于：

1. 服务器环境；
2. Python 开发；
3. 深度学习环境配置；
4. Docker、Git、Conda 等开发工具使用；
5. 云服务器和实验室服务器系统。

本阶段使用 Windows 下的 WSL Ubuntu。打开 Ubuntu 终端后，看到类似：

```bash
aku@Aku:~$
```

说明已经进入 Ubuntu/Linux 终端环境。

其中：

- `aku`：当前用户名；
- `Aku`：主机名；
- `~`：当前位于用户主目录；
- `$`：普通用户权限提示符。

---

## 1.5 Linux 内核和发行版

Linux 严格来说是一个操作系统内核。内核负责管理底层硬件资源，例如 CPU 调度、内存管理、文件系统、设备驱动、进程管理等。

但我们平时说“Linux 系统”，通常是指 Linux 发行版。发行版是在 Linux 内核基础上加入各种系统工具、软件包管理器和用户界面后形成的完整操作系统。

常见 Linux 发行版包括：

- Ubuntu
- Debian
- CentOS
- Fedora
- Arch Linux
- Red Hat

Linux 内核和发行版之间的关系可以理解为：

```text
硬件
  ↓
Linux 内核
  ↓
Linux 发行版
  ↓
用户和应用程序
```

本阶段学习的 Ubuntu 就是 Linux 发行版之一。后续深度学习服务器上也经常使用 Ubuntu 系统，因此掌握 Ubuntu/Linux 基础命令很重要。

---

## 1.6 查看目录命令

查看目录内容常用命令包括：

```bash
ls
tree
pwd
clear
```

### 1.6.1 ls 命令

`ls` 用于查看当前目录下的文件和文件夹。

```bash
ls
```

示例：

```bash
ls
```

如果当前目录下有文件 `1.txt` 和目录 `AA`，输出可能为：

```text
1.txt  AA
```

### 1.6.2 tree 命令

`tree` 可以以树状结构显示目录内容。

```bash
tree
tree AA
```

如果系统提示：

```text
Command 'tree' not found
```

说明没有安装 `tree`，可以安装：

```bash
sudo apt install tree -y
```

如果不想安装，也可以用：

```bash
ls -R
```

递归查看目录内容。

### 1.6.3 pwd 命令

`pwd` 用于查看当前所在目录的绝对路径。

```bash
pwd
```

例如输出：

```bash
/home/aku
```

说明当前位于 `/home/aku` 目录。

### 1.6.4 clear 命令

`clear` 用于清空终端屏幕显示内容。

```bash
clear
```

它不会删除文件，只是清理当前终端显示。

---

## 1.7 切换目录命令

切换目录主要使用 `cd` 命令。

```bash
cd 目录名
```

常见用法如下：

| 命令 | 含义 |
|---|---|
| `cd 目录名` | 进入指定目录 |
| `cd ..` | 返回上一级目录 |
| `cd ~` | 返回当前用户主目录 |
| `cd /` | 进入根目录 |
| `cd -` | 返回上一次所在目录 |

示例：

```bash
cd ~/dl-learning-notes
```

表示进入当前用户主目录下的 `dl-learning-notes` 文件夹。

```bash
cd ..
```

表示返回上一级目录。

```bash
cd ~
```

表示回到当前用户主目录。

注意：

- `cd` 后面如果什么都不写，默认回到当前用户主目录；
- Linux 区分大小写，`A` 和 `a` 是不同目录；
- 路径中如果有空格，需要加引号或使用转义符。

---

## 1.8 绝对路径和相对路径

Linux 中路径分为绝对路径和相对路径。

### 1.8.1 绝对路径

绝对路径从根目录 `/` 开始写，表示文件或目录在系统中的完整位置。

示例：

```bash
/home/aku/dl-learning-notes
/root/autodl-tmp/d2l-learning
```

绝对路径的特点是：无论当前在哪个目录，都可以准确定位目标文件或目录。

### 1.8.2 相对路径

相对路径是相对于当前所在目录的位置。

例如当前在：

```bash
/home/aku
```

如果要进入 `dl-learning-notes` 文件夹，可以写：

```bash
cd dl-learning-notes
```

这就是相对路径。

### 1.8.3 常用路径符号

| 符号 | 含义 |
|---|---|
| `.` | 当前目录 |
| `..` | 上一级目录 |
| `~` | 当前用户主目录 |
| `/` | 根目录 |

示例：

```bash
cd .
cd ..
cd ~
cd /
```

如果文件路径很明确，使用绝对路径更稳；如果当前就在相关目录附近，使用相对路径更方便。

例如：

```bash
cd /home/aku/dl-learning-notes
```

是绝对路径。

```bash
cd dl-learning-notes
```

是相对路径，前提是当前已经在 `/home/aku` 下。

---

## 1.9 创建、删除文件和目录

### 1.9.1 创建文件：touch

`touch` 可以创建空文件。

```bash
touch 文件名
```

示例：

```bash
touch 1.txt
touch 1.txt 2.txt
```

表示创建 `1.txt` 和 `2.txt` 两个文件。

### 1.9.2 创建目录：mkdir

`mkdir` 用于创建目录。

```bash
mkdir 目录名
```

示例：

```bash
mkdir AA
mkdir AA BB
```

表示创建 `AA` 和 `BB` 两个目录。

如果要创建多级目录，可以使用：

```bash
mkdir -p A/B/C
```

其中 `-p` 表示如果中间目录不存在，就自动创建。

### 1.9.3 删除文件：rm

`rm` 用于删除文件。

```bash
rm 文件名
```

示例：

```bash
rm 1.txt
```

### 1.9.4 删除空目录：rmdir

`rmdir` 只能删除空目录。

```bash
rmdir AA
```

如果目录中有文件，`rmdir` 无法删除。

### 1.9.5 删除目录及其中内容：rm -r

如果要删除目录及目录中的内容，可以使用：

```bash
rm -r 目录名
```

示例：

```bash
rm -r AA
```

### 1.9.6 强制删除：rm -rf

```bash
rm -rf 目录名
```

说明：

- `-r` 表示递归删除目录；
- `-f` 表示强制删除，不提示确认。

该命令风险较高，尤其不要乱用：

```bash
rm -rf /
```

这类命令可能造成严重后果。

---

## 1.10 拷贝、移动文件和目录

### 1.10.1 拷贝文件：cp

`cp` 用于复制文件。

```bash
cp 源文件 目标位置
```

示例：

```bash
cp 1.txt AA
```

表示把 `1.txt` 复制到 `AA` 目录中。

### 1.10.2 拷贝并改名

```bash
cp 1.txt 2.txt
```

表示复制 `1.txt`，并命名为 `2.txt`。

### 1.10.3 拷贝目录：cp -r

如果要复制目录，需要加 `-r`：

```bash
cp -r AA BB
```

表示把 `AA` 目录复制到 `BB` 目录中。

### 1.10.4 移动文件：mv

`mv` 可以移动文件或目录。

```bash
mv 文件名 目标目录
```

示例：

```bash
mv 1.txt AA
```

表示把 `1.txt` 移动到 `AA` 目录中。

### 1.10.5 重命名文件

`mv` 也可以用于重命名。

```bash
mv old.txt new.txt
```

表示把 `old.txt` 改名为 `new.txt`。

### 1.10.6 实际练习示例

```bash
touch 1.txt 2.txt
mkdir AA BB
cp 1.txt AA
ls AA
```

输出：

```text
1.txt
```

说明文件已经复制成功。

---

## 1.11 终端命令的格式说明

Linux 终端命令通常由三部分组成：

```bash
command [-options] [parameter]
```

也可以理解为：

```bash
命令 [选项] [参数]
```

例如：

```bash
ls -l /home
```

其中：

- `ls` 是命令；
- `-l` 是选项；
- `/home` 是参数。

### 1.11.1 命令

命令表示要执行的操作，例如：

```bash
ls
cd
mkdir
rm
cp
mv
```

### 1.11.2 选项

选项用于调整命令的功能。

短选项一般用一个短横线：

```bash
ls -l
ls -a
rm -r
```

长选项一般用两个短横线：

```bash
ls --help
mkdir --help
rm --help
```

### 1.11.3 参数

参数通常表示命令作用的对象，例如文件名、目录名、路径等。

```bash
cp 1.txt AA
```

其中 `1.txt` 和 `AA` 都是参数。

### 1.11.4 使用注意

有些命令可以没有选项和参数，例如：

```bash
pwd
ls
```

有些命令必须带参数，例如：

```bash
cd 目录名
cp 源文件 目标位置
```

---

## 1.12 查看命令帮助

学习 Linux 命令时，如果忘记命令怎么用，可以查看帮助。

### 1.12.1 使用 --help

```bash
命令 --help
```

示例：

```bash
ls --help
mkdir --help
rm --help
cp --help
```

`--help` 一般显示命令的基本用法和常用选项。

### 1.12.2 使用 man 手册

```bash
man 命令
```

示例：

```bash
man ls
man cp
man rm
```

`man` 是 manual 的缩写，内容通常比 `--help` 更完整。

进入 `man` 页面后：

- 按 `q` 退出；
- 按空格向下翻页；
- 按 `b` 向上翻页。

### 1.12.3 学习理解

`--help` 适合快速查用法；`man` 适合查看更完整的命令说明。

---

## 1.13 ls 命令选项

`ls` 用于查看目录内容。

### 1.13.1 基本用法

```bash
ls
```

### 1.13.2 显示隐藏文件：-a

```bash
ls -a
```

Linux 中以 `.` 开头的文件是隐藏文件，例如：

```text
.bashrc
.git
```

### 1.13.3 详细列表显示：-l

```bash
ls -l
```

输出中通常包含：

- 文件类型和权限；
- 所属用户；
- 所属组；
- 文件大小；
- 修改时间；
- 文件名。

### 1.13.4 文件大小更易读：-h

```bash
ls -lh
```

`-h` 通常和 `-l` 一起使用，可以用 KB、MB 等更容易理解的单位显示文件大小。

### 1.13.5 组合使用

```bash
ls -al
ls -lh
ls -alh
```

常用组合：

| 命令 | 作用 |
|---|---|
| `ls` | 查看当前目录内容 |
| `ls -a` | 查看所有文件，包括隐藏文件 |
| `ls -l` | 详细列表显示 |
| `ls -lh` | 以更易读方式显示大小 |
| `ls -alh` | 显示所有文件的详细信息，并以易读单位显示大小 |

---

## 1.14 mkdir 和 rm 命令选项

### 1.14.1 mkdir 命令选项

`mkdir` 用于创建目录。

创建单个目录：

```bash
mkdir AA
```

创建多个目录：

```bash
mkdir AA BB CC
```

创建多级目录：

```bash
mkdir -p A/B/C
```

如果 `A`、`B` 不存在，系统会自动创建。

查看 `mkdir` 帮助：

```bash
mkdir --help
```

### 1.14.2 rm 命令选项

`rm` 用于删除文件或目录。

删除文件：

```bash
rm 1.txt
```

删除目录：

```bash
rm -r AA
```

`-r` 表示递归删除目录及其中内容。

强制删除文件：

```bash
rm -f 1.txt
```

`-f` 表示强制删除，不提示确认。

强制递归删除目录：

```bash
rm -rf AA
```

说明：

- `-r`：递归删除；
- `-f`：强制删除。

`rm` 删除后的文件一般不会进入回收站，所以使用时要特别小心。尤其是 `rm -rf`，必须确认路径正确后再执行。

---

## 1.15 cp 和 mv 命令选项

### 1.15.1 cp 命令选项

`cp` 用于复制文件或目录。

复制文件：

```bash
cp 1.txt 2.txt
```

表示复制 `1.txt` 并生成 `2.txt`。

复制文件到目录：

```bash
cp 1.txt AA
```

表示将 `1.txt` 复制到 `AA` 目录中。

复制目录：

```bash
cp -r AA BB
```

表示递归复制目录。

交互式复制：

```bash
cp -i 1.txt AA
```

如果目标位置已有同名文件，会提示是否覆盖。

保留文件属性：

```bash
cp -p 1.txt 2.txt
```

保留文件的时间、权限等属性。

常用选项总结：

| 选项 | 作用 |
|---|---|
| `-r` | 递归复制目录 |
| `-i` | 覆盖前提示 |
| `-p` | 保留文件属性 |

### 1.15.2 mv 命令选项

`mv` 用于移动文件或目录，也可以用于重命名。

移动文件：

```bash
mv 1.txt AA
```

重命名文件：

```bash
mv 1.txt new.txt
```

移动目录：

```bash
mv AA BB
```

如果 `BB` 已存在，则把 `AA` 移动到 `BB` 目录中；如果 `BB` 不存在，则可能把 `AA` 重命名为 `BB`。

交互式移动：

```bash
mv -i 1.txt AA
```

如果目标位置存在同名文件，会提示是否覆盖。

---

## 1.16 重定向

重定向用于改变命令输入或输出的方向。常见的是把命令输出写入文件。

### 1.16.1 覆盖写入：>

```bash
echo "hello linux" > 1.txt
```

表示把 `hello linux` 写入 `1.txt`。如果 `1.txt` 原来有内容，会被覆盖。

### 1.16.2 追加写入：>>

```bash
echo "second line" >> 1.txt
```

表示把内容追加到 `1.txt` 文件末尾，不会覆盖原内容。

### 1.16.3 将命令结果写入文件

```bash
ls > list.txt
```

表示把 `ls` 的输出结果保存到 `list.txt`。

```bash
ls -l >> list.txt
```

表示把 `ls -l` 的输出结果追加到 `list.txt` 后面。

### 1.16.4 查看效果

```bash
cat 1.txt
cat list.txt
```

### 1.16.5 学习理解

`>` 和 `>>` 的区别：

| 符号 | 作用 |
|---|---|
| `>` | 覆盖写入 |
| `>>` | 追加写入 |

---

## 1.17 查看文件内容命令

常用查看文件内容命令包括：

```bash
cat
more
less
head
tail
```

### 1.17.1 cat 命令

`cat` 可以一次性查看文件全部内容。

```bash
cat 1.txt
```

也可以查看多个文件：

```bash
cat 1.txt 2.txt
```

如果文件内容很短，适合用 `cat`。

### 1.17.2 more 命令

`more` 可以分页查看较长文件。

```bash
more long.txt
```

常用操作：

- 空格：下一页；
- 回车：下一行；
- `q`：退出。

### 1.17.3 less 命令

`less` 也用于分页查看文件，比 `more` 更灵活。

```bash
less long.txt
```

常用操作：

- 空格：下一页；
- `b`：上一页；
- `/关键词`：搜索；
- `q`：退出。

### 1.17.4 head 命令

`head` 查看文件开头部分。

```bash
head 1.txt
head -n 5 1.txt
```

表示查看前 5 行。

### 1.17.5 tail 命令

`tail` 查看文件末尾部分。

```bash
tail 1.txt
tail -n 5 1.txt
```

表示查看最后 5 行。

实时查看日志常用：

```bash
tail -f log.txt
```

### 1.17.6 小结

| 命令 | 作用 |
|---|---|
| `cat` | 查看短文件全部内容 |
| `more` | 分页查看文件 |
| `less` | 更灵活地分页查看文件 |
| `head` | 查看文件开头 |
| `tail` | 查看文件结尾 |
| `tail -f` | 实时查看文件新增内容 |

---

## 1.18 软链接

软链接类似于 Windows 中的快捷方式。它保存的是目标文件或目录的路径，而不是文件本身的数据。

创建软链接使用：

```bash
ln -s 源文件路径 软链接名
```

示例：

```bash
ln -s /home/aku/test/hello.txt hello_link.txt
```

表示创建一个指向 `hello.txt` 的软链接。

查看链接：

```bash
ls -l
```

软链接通常会显示类似：

```text
hello_link.txt -> /home/aku/test/hello.txt
```

### 1.18.1 软链接特点

1. 可以链接文件，也可以链接目录；
2. 类似快捷方式；
3. 删除软链接不会删除源文件；
4. 如果源文件被删除，软链接会失效；
5. 软链接可以跨文件系统。

如果软链接和源文件不在同一个目录，建议使用绝对路径创建软链接，这样不容易失效。

---

## 1.19 硬链接

硬链接可以理解为给同一个文件数据起了另一个名字。硬链接和原文件指向同一份文件数据。

创建硬链接使用：

```bash
ln 源文件 硬链接名
```

示例：

```bash
ln hello.txt hello_hard.txt
```

表示为 `hello.txt` 创建一个硬链接 `hello_hard.txt`。

### 1.19.1 硬链接特点

1. 硬链接和源文件指向同一份数据；
2. 修改任意一个文件，另一个看到的内容也会变化；
3. 删除源文件后，只要还有硬链接存在，文件数据仍然可以访问；
4. 不能给目录创建硬链接；
5. 通常不能跨文件系统创建硬链接。

### 1.19.2 硬链接和软链接区别

| 对比项 | 软链接 | 硬链接 |
|---|---|---|
| 类似对象 | 快捷方式 | 文件的另一个名字 |
| 是否可链接目录 | 可以 | 通常不可以 |
| 源文件删除后 | 软链接失效 | 仍可访问数据 |
| 是否可跨文件系统 | 可以 | 通常不可以 |
| 创建命令 | `ln -s 源文件 链接名` | `ln 源文件 链接名` |

---

## 1.20 文本搜索命令

文本搜索主要使用 `grep` 命令。

```bash
grep 关键词 文件名
```

示例：

```bash
grep hello 1.txt
```

表示在 `1.txt` 中查找包含 `hello` 的行。

### 1.20.1 忽略大小写：-i

```bash
grep -i hello 1.txt
```

表示搜索时不区分大小写。

### 1.20.2 显示行号：-n

```bash
grep -n hello 1.txt
```

表示显示匹配内容所在行号。

### 1.20.3 反向查找：-v

```bash
grep -v hello 1.txt
```

表示显示不包含 `hello` 的行。

### 1.20.4 递归搜索目录：-r

```bash
grep -r hello .
```

表示在当前目录及其子目录中递归搜索 `hello`。

### 1.20.5 结合管道使用

```bash
ls -l | grep txt
```

表示先执行 `ls -l`，再从结果中筛选包含 `txt` 的行。

### 1.20.6 常用选项总结

| 命令 | 作用 |
|---|---|
| `grep 关键词 文件` | 搜索包含关键词的行 |
| `grep -i` | 忽略大小写 |
| `grep -n` | 显示行号 |
| `grep -v` | 显示不包含关键词的行 |
| `grep -r` | 递归搜索目录 |

---

## 1.21 查找文件命令

查找文件常用 `find` 命令。

基本格式：

```bash
find 查找路径 条件
```

### 1.21.1 按文件名查找

```bash
find . -name "1.txt"
```

表示在当前目录下查找名为 `1.txt` 的文件。

### 1.21.2 使用通配符查找

```bash
find . -name "*.txt"
```

表示查找所有 `.txt` 文件。

### 1.21.3 忽略大小写查找

```bash
find . -iname "*.txt"
```

`-iname` 表示忽略大小写。

### 1.21.4 按类型查找

查找普通文件：

```bash
find . -type f
```

查找目录：

```bash
find . -type d
```

### 1.21.5 查找后执行命令

例如查找所有 `.txt` 文件并显示：

```bash
find . -name "*.txt" -print
```

### 1.21.6 学习理解

`find` 适合在目录层级较多、文件数量较大时快速定位目标文件。

---

## 1.22 压缩和解压缩命令

Linux 中常见压缩格式包括：

- `.tar`
- `.gz`
- `.tar.gz`
- `.zip`

### 1.22.1 tar 打包

`tar` 可以把多个文件打包成一个文件。

```bash
tar -cvf archive.tar file1 file2 dir1
```

含义：

- `-c`：创建打包文件；
- `-v`：显示过程；
- `-f`：指定文件名。

### 1.22.2 tar 解包

```bash
tar -xvf archive.tar
```

含义：

- `-x`：解包；
- `-v`：显示过程；
- `-f`：指定文件名。

### 1.22.3 tar.gz 压缩

```bash
tar -zcvf archive.tar.gz dir1
```

其中：

- `-z`：使用 gzip 压缩；
- `-c`：创建；
- `-v`：显示过程；
- `-f`：指定文件名。

### 1.22.4 tar.gz 解压

```bash
tar -zxvf archive.tar.gz
```

### 1.22.5 zip 压缩

```bash
zip archive.zip 1.txt 2.txt
```

压缩目录：

```bash
zip -r archive.zip AA
```

### 1.22.6 unzip 解压

```bash
unzip archive.zip
```

解压到指定目录：

```bash
unzip archive.zip -d target_dir
```

### 1.22.7 常用命令总结

| 命令 | 作用 |
|---|---|
| `tar -cvf a.tar 文件/目录` | 打包 |
| `tar -xvf a.tar` | 解包 |
| `tar -zcvf a.tar.gz 目录` | 打包并 gzip 压缩 |
| `tar -zxvf a.tar.gz` | 解压 tar.gz |
| `zip a.zip 文件` | zip 压缩文件 |
| `zip -r a.zip 目录` | zip 压缩目录 |
| `unzip a.zip` | 解压 zip 文件 |

---

## 1.23 文件权限命令

Linux 中每个文件和目录都有权限。可以用：

```bash
ls -l
```

查看权限。

输出示例：

```text
-rw-r--r-- 1 aku aku 100 May 20 1.txt
```

最前面的权限部分可以拆分理解：

```text
- rw- r-- r--
```

第一位表示文件类型：

| 符号 | 含义 |
|---|---|
| `-` | 普通文件 |
| `d` | 目录 |
| `l` | 链接文件 |

后面 9 位分为三组：

```text
所有者权限  所属组权限  其他用户权限
rwx        rwx       rwx
```

权限含义：

| 权限 | 含义 | 数字 |
|---|---|---|
| `r` | read，读权限 | 4 |
| `w` | write，写权限 | 2 |
| `x` | execute，执行权限 | 1 |

### 1.23.1 chmod 字母法

修改权限可以使用 `chmod`。

```bash
chmod u+x file.sh
```

表示给文件所有者增加执行权限。

常见对象：

| 符号 | 含义 |
|---|---|
| `u` | user，文件所有者 |
| `g` | group，所属组 |
| `o` | other，其他用户 |
| `a` | all，所有用户 |

操作符：

| 符号 | 含义 |
|---|---|
| `+` | 增加权限 |
| `-` | 删除权限 |
| `=` | 设置权限 |

示例：

```bash
chmod u+x test.sh
chmod g-w 1.txt
chmod o=r 1.txt
chmod a+r 1.txt
```

### 1.23.2 chmod 数字法

权限数字含义：

```text
r = 4
w = 2
x = 1
```

常见组合：

| 数字 | 权限 |
|---|---|
| `7` | `rwx` |
| `6` | `rw-` |
| `5` | `r-x` |
| `4` | `r--` |
| `0` | `---` |

例如：

```bash
chmod 755 test.sh
```

表示：

```text
所有者：rwx = 7
所属组：r-x = 5
其他人：r-x = 5
```

```bash
chmod 644 1.txt
```

表示：

```text
所有者：rw- = 6
所属组：r-- = 4
其他人：r-- = 4
```

### 1.23.3 学习理解

权限控制可以保护文件安全，避免误修改或误执行。脚本文件如果需要执行，通常要添加执行权限：

```bash
chmod +x script.sh
./script.sh
```

---

## 1.24 获取管理权限的相关命令

Linux 中普通用户权限有限，涉及安装软件、修改系统目录等操作时，需要管理员权限。

### 1.24.1 sudo 命令

`sudo` 可以临时以管理员权限执行命令。

```bash
sudo apt update
sudo apt install tree -y
```

第一次使用 `sudo` 时，系统会要求输入当前用户密码。

### 1.24.2 切换到 root：sudo -s

```bash
sudo -s
```

执行后，可能从普通用户变成 root 用户，提示符可能从 `$` 变成 `#`。

普通用户提示符：

```bash
aku@Aku:~$
```

root 用户提示符：

```bash
root@Aku:~#
```

`#` 表示当前拥有更高权限。

### 1.24.3 查看当前用户：whoami

```bash
whoami
```

如果输出：

```text
aku
```

说明当前是普通用户。

如果输出：

```text
root
```

说明当前是 root 用户。

### 1.24.4 查看登录用户：who

```bash
who
```

可以查看当前登录到系统的用户信息。

### 1.24.5 修改密码：passwd

```bash
passwd
```

可以修改当前用户密码。

如果是 root 用户，也可以修改其他用户密码：

```bash
passwd 用户名
```

### 1.24.6 管理权限使用注意

管理员权限很强，可以修改系统关键文件，也可能误删重要内容。因此使用 `sudo` 和 root 权限时需要谨慎。

尤其不要随意执行危险命令，例如：

```bash
sudo rm -rf /
```

### 1.24.7 学习理解

`sudo` 的作用是临时提升权限，不是所有命令都需要加 `sudo`。只有在普通用户权限不足时，例如安装软件、修改系统目录，才需要使用 `sudo`。

---

## 1.25 Linux 基础命令学习小结

通过本阶段学习，我初步掌握了 Linux 操作系统的基础概念和常用命令，包括：

1. 操作系统、虚拟机、Ubuntu、Linux 内核和发行版的基本关系；
2. 目录查看、目录切换、路径表示方法；
3. 文件和目录的创建、删除、复制、移动和重命名；
4. 终端命令的基本格式；
5. 使用 `--help` 和 `man` 查看命令帮助；
6. 使用 `ls`、`mkdir`、`rm`、`cp`、`mv` 等命令选项；
7. 使用重定向将命令输出写入文件；
8. 使用 `cat`、`more`、`less`、`head`、`tail` 查看文件内容；
9. 理解软链接和硬链接的区别；
10. 使用 `grep` 搜索文本；
11. 使用 `find` 查找文件；
12. 使用 `tar`、`zip`、`unzip` 进行压缩和解压；
13. 使用 `chmod` 管理文件权限；
14. 使用 `sudo`、`whoami`、`who`、`passwd` 等命令处理管理权限相关问题。

后续需要继续结合实际代码开发和深度学习环境配置，熟练使用这些 Linux 命令。

---

# 2. Conda、CUDA、cuDNN 环境搭建

## 2.1 当前完成情况

本部分目前还未完整完成。后续需要继续学习并记录 Conda 的本地安装和配置过程。

目前已经了解的内容如下：

- Conda 用于 Python 环境管理；
- CUDA 是 NVIDIA 提供的 GPU 并行计算平台；
- cuDNN 是 NVIDIA 针对深度学习的 GPU 加速库；
- PyTorch、TensorFlow 等深度学习框架在使用 NVIDIA GPU 训练时，通常需要 CUDA/cuDNN 支持。

---

## 2.2 本机硬件情况说明

通过 Windows 任务管理器查看，本机 GPU 为：

```text
Intel(R) Iris(R) Xe Graphics
```

该显卡属于 Intel 核显，不是 NVIDIA 独立显卡。虽然 Intel Iris Xe Graphics 也属于 GPU，但它不支持 NVIDIA CUDA/cuDNN 生态。

深度学习课程中常见的 CUDA 和 cuDNN 主要用于 NVIDIA GPU 加速训练。因此，本机不具备本地配置 CUDA/cuDNN 的条件。

任务管理器中显示的共享 GPU 内存并不是独立显存，而是核显临时借用的系统内存。因此，本机更适合用于：

1. Linux 基础学习；
2. Python 基础学习；
3. Git 和 GitHub 使用；
4. VS Code 开发环境熟悉；
5. Conda 环境管理；
6. CPU 版 PyTorch 学习；
7. 小规模代码调试。

后续如果需要进行 Transformer、VLM 等深度学习模型训练，应使用实验室服务器或云端 NVIDIA GPU 服务器完成。

---

## 2.3 当前学习阶段是否必须使用 CUDA/cuDNN

当前主要学习内容包括：

- Linux 基础；
- Python 基础；
- Git 与 GitHub；
- 李沐《动手学深度学习》课程；
- PyTorch 基础；
- 论文阅读。

这些内容在入门阶段并不是必须依赖 CUDA/cuDNN。对于线性回归、softmax 回归、多层感知机、小规模 CNN 等内容，CPU 环境也可以完成学习和调试。

CUDA/cuDNN 更适合在后续训练较大模型时使用，例如：

- ResNet；
- Transformer；
- BERT；
- ViT；
- VLM；
- 大规模数据训练；
- 论文复现中的完整训练实验。

因此，当前阶段的策略是：

```text
本机 WSL Ubuntu + VS Code + Conda + CPU 版 PyTorch
云端 AutoDL GPU + CUDA + PyTorch 用于需要 GPU 的实验
```

---

## 2.4 后续计划

后续需要继续完成：

1. Miniconda 或 Anaconda 安装；
2. Conda 创建虚拟环境；
3. Conda 环境激活与退出；
4. CPU 版本 PyTorch 安装；
5. 在云端 GPU 上学习 CUDA/PyTorch 环境检查；
6. 在 VS Code Remote-SSH 中运行 GPU 代码。

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

如果输出 `False`，说明当前没有检测到 CUDA GPU，这对于本机 Intel 核显环境是正常情况。

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

# 6. AutoDL 云端 GPU 环境配置与使用记录

## 6.1 使用云端 GPU 的原因

本机显卡为 Intel Iris Xe 核显，没有 NVIDIA 独立显卡，因此无法在本地配置 CUDA/cuDNN GPU 深度学习环境。

为了后续学习李沐《动手学深度学习》、PyTorch、论文复现和深度学习模型训练，本阶段尝试使用 AutoDL 云端 GPU 实例。这样可以实现：

- 本地电脑不用安装 CUDA/cuDNN；
- 云端服务器提供 NVIDIA GPU；
- 云端镜像预装 PyTorch、CUDA 等深度学习环境；
- 本地通过 SSH 或 VS Code Remote-SSH 连接云端服务器；
- 代码实际在云端 GPU 上运行。

---

## 6.2 租用 AutoDL 云端 GPU 实例

进入 AutoDL 官网并登录账号后，在算力市场中选择一台 GPU 实例。

本次测试租用的云端实例配置如下：

| 项目 | 配置 |
|---|---|
| 平台 | AutoDL |
| 系统 | Ubuntu 22.04 |
| GPU | NVIDIA GeForce RTX 4080 SUPER |
| GPU 数量 | 1 |
| CPU | 12 核 |
| 内存 | 62 GB |
| 系统盘 | 30 GB |
| 数据盘 | 50 GB |
| PyTorch | 2.3.0+cu121 |
| CUDA | PyTorch 对应 CUDA 12.1，驱动显示 CUDA Version 13.2 |

租用实例时选择按量计费。实例开机后，状态显示为“运行中”，此时开始计费。

---

## 6.3 SSH 登录云端服务器

实例启动后，AutoDL 页面提供 SSH 登录指令和密码。

本次使用的 SSH 登录指令格式为：

```bash
ssh -p 33984 root@connect.weste.seetacloud.com
```

在 Windows PowerShell 中输入该命令：

```powershell
ssh -p 33984 root@connect.weste.seetacloud.com
```

第一次连接时，终端提示：

```text
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

输入：

```text
yes
```

然后输入 AutoDL 页面提供的密码。密码输入过程中终端不会显示字符，这是正常现象。

登录成功后，终端显示类似：

```bash
root@autodl-container-xxx:~#
```

说明已经进入云端 Linux 服务器。

---

## 6.4 AutoDL 目录说明

登录后，AutoDL 提示了两个重要目录：

| 目录 | 说明 |
|---|---|
| `/` | 系统盘，空间较小，适合放少量配置和代码 |
| `/root/autodl-tmp` | 数据盘，读写速度快，适合存放代码、数据集和实验文件 |

因此，本次将学习代码放在数据盘中：

```bash
mkdir -p /root/autodl-tmp/d2l-learning
cd /root/autodl-tmp/d2l-learning
```

检查当前路径：

```bash
pwd
```

输出为：

```bash
/root/autodl-tmp/d2l-learning
```

---

## 6.5 检查云端 GPU

在云端服务器终端中输入：

```bash
nvidia-smi
```

输出结果显示服务器识别到：

```text
NVIDIA GeForce RTX 4080 SUPER
```

同时可以看到驱动版本和 CUDA Version，说明云端 NVIDIA GPU 可用。

---

## 6.6 检查 Conda 环境

输入：

```bash
conda env list
```

输出显示：

```text
base    /root/miniconda3
```

说明云端镜像中已经安装了 Miniconda，并且当前存在 `base` 环境。

---

## 6.7 测试 PyTorch 是否可以调用 GPU

首先进入 Python：

```bash
python
```

在 Python 交互环境中输入：

```python
import torch
print(torch.__version__)
print(torch.cuda.is_available())
```

输出结果为：

```text
2.3.0+cu121
True
```

其中：

- `2.3.0+cu121` 表示当前 PyTorch 版本为 2.3.0，并且是 CUDA 12.1 版本；
- `True` 表示 PyTorch 可以检测并调用 CUDA GPU。

退出 Python：

```python
exit()
```

---

## 6.8 创建 GPU 测试脚本

在 `/root/autodl-tmp/d2l-learning` 目录下创建测试文件：

```bash
cat > test_gpu.py <<'PY'
import torch

print("PyTorch version:", torch.__version__)
print("CUDA available:", torch.cuda.is_available())

if torch.cuda.is_available():
    print("GPU name:", torch.cuda.get_device_name(0))
    x = torch.randn(1000, 1000).cuda()
    y = x @ x
    print("Tensor device:", y.device)
PY
```

运行测试脚本：

```bash
python test_gpu.py
```

输出结果为：

```text
PyTorch version: 2.3.0+cu121
CUDA available: True
GPU name: NVIDIA GeForce RTX 4080 SUPER
Tensor device: cuda:0
```

该结果说明：

1. PyTorch 已成功安装；
2. CUDA 可以被 PyTorch 调用；
3. GPU 为 NVIDIA GeForce RTX 4080 SUPER；
4. 张量计算实际运行在 `cuda:0` 上。

因此，云端 GPU 深度学习环境测试成功。

---

## 6.9 VS Code Remote-SSH 连接云端服务器

为了实现在本地 VS Code 中写代码、在云端 GPU 上运行代码，需要使用 VS Code 的 Remote-SSH 插件。

### 6.9.1 安装 Remote-SSH 插件

在本地 Windows 的 VS Code 中打开扩展市场，搜索并安装：

```text
Remote - SSH
```

安装完成后，可以通过 VS Code 连接远程 Linux 服务器。

### 6.9.2 添加 SSH 主机

在 VS Code 中按：

```text
F1
```

搜索：

```text
Remote-SSH: Add New SSH Host
```

输入 AutoDL 提供的 SSH 指令：

```bash
ssh -p 33984 root@connect.weste.seetacloud.com
```

保存到默认 SSH 配置文件。

### 6.9.3 连接远程主机

再次按：

```text
F1
```

搜索：

```text
Remote-SSH: Connect to Host
```

选择：

```text
connect.weste.seetacloud.com
```

系统类型选择：

```text
Linux
```

然后输入 AutoDL 密码。

连接成功后，VS Code 左下角会显示类似：

```text
SSH: connect.weste.seetacloud.com
```

此时 VS Code 已经连接到云端服务器。

---

## 6.10 VS Code Server 下载卡住问题处理

第一次使用 VS Code Remote-SSH 连接时，可能会卡在：

```text
Downloading with wget
```

这是因为远程服务器下载 VS Code Server 较慢或失败。

解决方法如下。

首先，在 PowerShell 中登录云端服务器：

```powershell
ssh -p 33984 root@connect.weste.seetacloud.com
```

然后清理未安装完成的 VS Code Server：

```bash
rm -rf ~/.vscode-server
```

退出服务器：

```bash
exit
```

然后在本地 VS Code 中打开用户设置 JSON：

```text
Preferences: Open User Settings (JSON)
```

加入配置：

```json
"remote.SSH.localServerDownload": "always"
```

如果原文件为空，可以写成：

```json
{
    "remote.SSH.localServerDownload": "always"
}
```

该设置表示让本地 VS Code 下载 VS Code Server 后再上传到远程服务器，避免远程服务器直接下载卡住。

保存后，重新使用 Remote-SSH 连接 AutoDL。

---

## 6.11 下次重新使用云端 GPU 的流程

### 6.11.1 在 AutoDL 网页开机

进入 AutoDL 控制台，找到该实例。如果状态为：

```text
已关机
```

点击：

```text
开机
```

等待状态变为：

```text
运行中
```

只有实例处于运行中时，才能通过 SSH 或 VS Code 连接服务器。需要注意，实例运行中会产生计费。

---

### 6.11.2 使用 PowerShell 登录服务器

打开 Windows PowerShell，输入 AutoDL 提供的 SSH 登录命令：

```powershell
ssh -p 33984 root@connect.weste.seetacloud.com
```

然后输入 AutoDL 页面提供的密码。

登录成功后，终端会显示类似：

```bash
root@autodl-container-xxx:~#
```

说明已经进入云端 Linux 服务器。

---

### 6.11.3 进入代码目录

本次创建的代码目录位于数据盘：

```bash
/root/autodl-tmp/d2l-learning
```

下次登录服务器后，进入该目录：

```bash
cd /root/autodl-tmp/d2l-learning
```

检查当前路径：

```bash
pwd
```

如果输出为：

```bash
/root/autodl-tmp/d2l-learning
```

说明已经进入正确的代码目录。

---

### 6.11.4 检查 GPU 是否正常

输入：

```bash
nvidia-smi
```

如果可以看到 NVIDIA GeForce RTX 4080 SUPER 等显卡信息，说明云端 GPU 正常。

---

### 6.11.5 运行测试脚本

运行之前创建的 GPU 测试文件：

```bash
python test_gpu.py
```

如果输出中包含：

```text
CUDA available: True
Tensor device: cuda:0
```

说明 PyTorch 可以正常调用云端 GPU。

---

### 6.11.6 使用 VS Code 重新连接云端服务器

如果需要在 VS Code 中写代码，可以打开本地 VS Code，按：

```text
F1
```

搜索：

```text
Remote-SSH: Connect to Host
```

选择：

```text
connect.weste.seetacloud.com
```

输入 AutoDL 密码。

连接成功后，VS Code 左下角会显示类似：

```text
SSH: connect.weste.seetacloud.com
```

然后打开云端代码文件夹：

```text
/root/autodl-tmp/d2l-learning
```

之后就可以在 VS Code 中创建、修改 Python 文件，并在 VS Code 的远程终端中运行代码。

---

## 6.12 用完后的退出与关机

### 6.12.1 退出 SSH

如果是在 PowerShell 中连接服务器，使用完后输入：

```bash
exit
```

即可退出远程服务器，回到本地 PowerShell。

### 6.12.2 关闭 VS Code 远程连接

如果 VS Code 正在连接远程服务器，可以直接关闭远程窗口，也可以按：

```text
F1
```

搜索：

```text
Remote-SSH: Close Remote Connection
```

关闭远程连接。

### 6.12.3 回 AutoDL 网页关机

需要特别注意：

```text
退出 PowerShell 或关闭 VS Code，并不会停止 AutoDL 实例计费。
```

真正停止主要 GPU 计算费用，需要回到 AutoDL 网页，在实例页面点击：

```text
关机
```

等待实例状态变成：

```text
已关机
```

这才说明主要 GPU 计算费用已经停止。

因此，下次使用 AutoDL 云端 GPU 的完整流程可以总结为：

```text
AutoDL 网页开机
→ PowerShell 或 VS Code 连接服务器
→ cd /root/autodl-tmp/d2l-learning
→ nvidia-smi 检查 GPU
→ python test_gpu.py 测试 PyTorch
→ 编写和运行代码
→ exit 退出 SSH
→ AutoDL 网页关机
```

---

## 6.13 本部分学习理解

通过本次实践，我理解了本地开发和云端 GPU 计算之间的关系。

本地电脑主要负责：

1. 打开 VS Code；
2. 编辑代码；
3. 通过 SSH 连接远程服务器；
4. 保存学习笔记和管理 GitHub 仓库。

云端服务器负责：

1. 提供 NVIDIA GPU；
2. 提供 CUDA/cuDNN/PyTorch 环境；
3. 实际运行 Python 和深度学习代码；
4. 执行需要 GPU 加速的训练和测试任务。

因此，即使本机没有 NVIDIA 独立显卡，也可以通过 AutoDL 云端 GPU 实例完成深度学习实验。对于当前学习阶段，本地可以继续用于 Linux、Git、Python 基础学习，而涉及 GPU 的代码可以放到云端服务器运行。

---

# 7. Chapter 0 当前完成情况总结

| 项目 | 当前状态 | 说明 |
|---|---|---|
| Linux 环境搭建 | 已完成 | 已安装 WSL Ubuntu，并能使用 Ubuntu 终端 |
| VS Code 连接 Linux | 已完成 | 可通过 `code .` 打开 Linux 文件夹 |
| Linux 基础指令学习 | 进行中 | 已学习目录、路径、文件创建、删除、复制、移动等基础命令，后续继续补充 |
| Conda 环境搭建 | 未完成 | 本地 Conda 后续继续安装和记录 |
| CUDA/cuDNN | 本机不适合配置 | 本机为 Intel Iris Xe 核显，不支持 NVIDIA CUDA |
| 云端 GPU 环境 | 已完成初步测试 | 已使用 AutoDL RTX 4080 SUPER 测试 PyTorch GPU |
| 计算机网络 | 已整理基础知识 | 已理解公网、局域网、子网划分、服务器直连传输思路 |
| 科学上网 | 已完成本机与 WSL 代理配置 | WSL 可通过 7897 端口访问 GitHub |
| Git 使用 | 已完成基础流程 | 已能创建本地仓库并推送到 GitHub |
| Markdown 上传 GitHub | 已完成 | 已将 README.md 上传至 GitHub 仓库 |

---

# 8. 后续学习计划

1. 继续完成 Linux 基础指令学习，补充权限、压缩解压、进程管理、环境变量等内容；
2. 安装并学习 Conda，掌握虚拟环境创建、激活、删除和依赖管理；
3. 在本地 CPU 环境下测试 Python 和 PyTorch 基础代码；
4. 继续学习李沐《动手学深度学习》课程，优先理解张量、自动求导、线性回归、softmax 回归、多层感知机和卷积神经网络等基础内容；
5. 对于需要 GPU 的代码，使用 AutoDL 云端 GPU 环境运行；
6. 后续进一步学习 SSH 远程连接、VS Code Remote-SSH、云端代码管理和 GitHub 同步；
7. 持续使用 Markdown 记录学习过程，并通过 Git 上传到 GitHub。
