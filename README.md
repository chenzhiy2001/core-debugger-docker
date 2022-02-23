# CoreDebugger
这个Docker容器提供了在线vscode、[gdbgui](https://www.gdbgui.com/)、rust工具链以及`qemu-system-riscv64`等[rCore-Tutorial-v3](https://rcore-os.github.io/rCore-Tutorial-Book-v3/index.html)需要的工具。
只需要启动该容器，您就可以：
- 无需配置实验环境，直接开始学习[rCore-Tutorial-v3](https://rcore-os.github.io/rCore-Tutorial-Book-v3/index.html)（暂无文件存储功能，关闭容器前务必保存项目）
- 使用图形调试界面
## 如何使用
### 拉取镜像
`
docker pu
·
也可以自己构建。
### 自己构建
1. 在sifive[网站](https://www.sifive.com/software)下载[`riscv64-unknown-elf-toolchain-10.2.0-2020.12.8-x86_64-linux-ubuntu14.tar.gz`]（往下拉找到GNU Embedded Toolchain — v2020.12.8, 下载ubuntu版本），
或者试试直接访问
[这里](https://static.dev.sifive.com/dev-tools/riscv64-unknown-elf-gcc-8.3.0-2020.04.1-x86_64-linux-ubuntu14.tar.gz)。下载后将该文件复制到本项目的目录下。
2. 构建（大约需要半小时）
`
sudo docker build -t gdbgui-test . 
`
### 启动镜像
`
sudo docker run --cap-add=SYS_PTRACE --security-opt seccomp=unconfined -it --rm -v $PWD:/sharedFolder --name gdbgui-test-1 -p 3000:3000 -p 5000:5000  gdbgui-test 
`
运行后，终端会显示在线vscode的网页地址，一般是`localhost:3000`。

### 编译、运行、调试
1. 将`/home/workspace`中的PROJECT_NAME修改为您的的项目的文件夹名
2. （可选）使用[github镜像站](https://doc.fastgit.org/zh-cn/guide.html)
```makefile
make fast_github
```
2. 编译、运行
```makefile
make build_run_project
```
3. 调试
```makefile
make build_run_project
```

