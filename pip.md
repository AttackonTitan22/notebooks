## **pip 入门**

pip 是 Python 的包管理器。这意味着它是一个工具，允许你安装和管理不属于标准库的其他库和依赖。

Python 被认为是一种"内置电池"式的语言。这表示 Python 标准库包含大量的软件包和模块，这些模块有助于开发人员开发脚本和应用。

### pip 最常用命令

**显示版本和路径**

```
pip --version
```

**获取帮助**

```
pip --help
```

**升级 pip**

```
pip install -U pip
```

> 如果这个升级命令出现问题 ，可以使用以下命令：
>
> ```
> sudo easy_install --upgrade pip
> ```

**安装包**

```
pip install SomePackage              # 最新版本
pip install SomePackage==1.0.4       # 指定版本
pip install 'SomePackage>=1.0.4'     # 最小版本
```

比如我要安装 Django。用以下的一条命令就可以，方便快捷。

```
pip install Django==1.7
```

**升级包**

```
pip install --upgrade SomePackage
```

升级指定的包，通过使用==, >=, <=, >, < 来指定一个版本号。

**卸载包**

```
pip uninstall SomePackage
```

**搜索包**

```
pip search SomePackage
```

**显示安装包信息**

```
pip show 
```

**查看指定包的详细信息**

```
pip show -f SomePackage
```

**列出已安装的包**

```
pip list
```

**查看可升级的包**

```
pip list -o
```

### pip 升级

**Linux 或 macOS**

```
pip install --upgrade pip    # python2.x
pip3 install --upgrade pip   # python3.x
```

**Windows 平台升级：**

```
python -m pip install -U pip   # python2.x
python -m pip3 install -U pip    # python3.x
```

### pip 清华大学开源软件镜像站

使用国内镜像速度会快很多：

临时使用：

```
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple some-package
```

例如，安装 Django：

```
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple Django
```

如果要设为默认需要升级 pip 到最新的版本 (>=10.0.0) 后进行配置：

```
pip install pip -U
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```

如果您到 pip 默认源的网络连接较差，临时使用本镜像站来升级 pip：

```
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple pip -U
```

### 注意事项

如果 Python2 和 Python3 同时有 pip，则使用方法如下：

Python2：

```
python2 -m pip install XXX
```

Python3:

```
python3 -m pip install XXX
```

若由于一些局域网的原因，使用 pip 出现 “connection timeout”，连接超时可以使用国内的镜像网站下载：

-  豆瓣：https://pypi.doubanio.com/simple/
-  清华：https://pypi.tuna.tsinghua.edu.cn/simple

命令如下:

```
pip install -i http://pypi.douban.com/simple --trusted-host pypi.douban.com packagename # packagename是要下载的包的名字
pip install -i http://e.pypi.python.org --trusted-host e.pypi.python.org --upgrade pip # 升级pip
```

## 对于pip、conda、anaconda和miniconda的区别。

```
conda是一个包和环境管理工具，它不仅能管理包，还能隔离和管理不同python版本的环境。类似管理nodejs环境的nvm工具。
anaconda和miniconda都是conda的一种发行版。只是包含的包不同。
anaconda包含了conda、python等180多个科学包及其依赖项，体格比较大。
miniconda是最小的conda安装环境，只有conda+python+pip+zlib和一些其他常用的包，体格非常迷你。
pip也叫包管理器，和conda的区别是，pip只管理python的包，而conda可以安装所有语言的包。而且conda可以管理python环境，pip不行。
```

```
pip freeze > requirements.txt    #按照格式化输出以已经安装的软件包。你可以使用这个命令，将输出重定向到文件以生成一个需求文件
pip install -r requirements.txt   #软件包的版本会根据 requirements.txt 所列出的进行匹配
pip uninstall -r requirements.txt -y 按需求卸载包，且-y是不展现信息
```

待用镜像

```
- https://mirrors.ustc.edu.cn/anaconda/cloud/conda-forge/
  - https://mirrors.ustc.edu.cn/anaconda/pkgs/free/
  - https://mirrors.ustc.edu.cn/anaconda/pkgs/main/
```

