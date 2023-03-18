# [pyenv](https://github.com/pyenv/pyenv)

## 预下载 Python 版本加速安装

### Linux/macos

1. 手动下载对应的 Python 版本，如通过镜像站。
2. 将下载的 Python 文件放到 `~/.pyenv/cache/` 目录下。
3. 执行 `pyenv install <version>` 安装。

例如：

```shell
version=x.y.z
wget "https://<mirrors.python.site>/$version/Python-$version.tar.xz" -P ~/.pyenv/cache/
pyenv install $version
```

### 可选下载源

- https://registry.npmmirror.com/-/binary/python/${version}/Python-${version}.tar.xz
- https://mirrors.huaweicloud.com/python/${version}/Python-${version}.tar.xz
