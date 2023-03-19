# SSH

## 代理

```shell
ssh -o ProxyCommand="ncat --proxy-type <proxy-type> --proxy <proxy-ip>:<proxy-port> %h %p" root@server
```

比如：

```shell
ssh -o ProxyCommand="ncat --proxy-type socks5 --proxy 127.0.0.1:1080 %h %p" root@server
```

搭配 Git 使用时，修改 `~/.ssh/config` 文件：

```
Host github.com
    # ncat --proxy-type socks5 --proxy 127.0.0.1:1080 %h %p
    # User git
    ncat --proxy 127.0.0.1:1081 %h %p
```
