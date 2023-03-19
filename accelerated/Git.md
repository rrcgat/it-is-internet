# Git

## 代理

```shell
git config --global http.proxy http://proxyUsername:proxyPassword@proxy.server.com:port
```

也可对单独域名设置代理：

```shell
git config --global http.https://domain.com.proxy http://proxyUsername:proxyPassword@proxy.server.com:port
# git config --global http.https://domain.com.sslVerify false
```

比如：

```shell
git config --global http.https://github.com.proxy http://127.0.0.1:1080
```

对应的 `~/.gitconfig` 内容：

```toml
[http "https://github.com"]
    proxy = http://127.0.0.1:1080
    ; proxy = socks5://127.0.0.1:1081
    ; proxy = socks5h://127.0.0.1:1081
    ; `h` 表示使用 socks5 代理解析 DNS，而不是本地的 DNS
```

对于使用 SSH 连接的仓库，需要配置 [SSH](./SSH.md) 代理。

---

- [Configure Git to use a proxy](https://gist.github.com/evantoli/f8c23a37eb3558ab8765)
- [git 设置和取消代理](https://gist.github.com/laispace/666dd7b27e9116faece6)
- [Differentiate socks5h from socks5 and socks4a from socks4 when handling proxy string](https://github.com/urllib3/urllib3/issues/1035)
- [Twitter - @skywind3000](https://twitter.com/skywind3000/status/1600163757304401921)
