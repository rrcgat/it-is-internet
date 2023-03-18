# It's Internet

通过一些配置，更优雅地访问互联网。

## 代理

通常的方式是设置代理。对于全局代理，一般不需要针对单个软件进行设置。对于非全局代理，终端工具需要设置对应的环境变量，比如：

```
http_proxy
https_proxy
all_proxy
HTTP_PROXY
HTTPS_PROXY
ALL_PROXY
...
```

不支持读取环境变量的程序，大多提供的对应的命令行参数，比如 `--proxy`，或者可使用 [proxychains](https://github.com/haad/proxychains)。

## 镜像

有时条件不允许或不方便设置代理，那么设置镜像是另一条路，比如 Docker 和 Python 的 pip。
