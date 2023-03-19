# [Docker](https://www.docker.com/)

## 镜像（`docker pull`）

1. 修改 `daemon.json`，Linux 下位于 `/etc/docker/` 目录下，macOS 中使用 Docker Desktop 修改。
2. 顶层配置添加 `registry-mirrors`，对应的值为数组，数组中的每个元素都是一个镜像源。
3. 重启 Docker 后生效。

修改后的 `daemon.json`：

```json
{
 "registry-mirrors" : [
   "https://mirror.ccs.tencentyun.com"
 ],
 ...
}
```

可用镜像源：

- https://hub-mirror.c.163.com
- https://dockerhub.azk8s.cn
- https://mirror.ccs.tencentyun.com

## 代理

> The Docker daemon uses the HTTP_PROXY, HTTPS_PROXY, and NO_PROXY environmental variables in its start-up environment to configure HTTP or HTTPS proxy behavior. You can’t configure these environment variables using the daemon.json file.

Docker daemon 依赖启动时的环境变量 `HTTP_PROXY` 和 `HTTPS_PROXY`，因此在启动后设置无效。

1. 创建或编辑 `http-proxy.conf`（位于 `/etc/systemd/system/docker.service.d`，rootless mode 启动的 Docker 则位于 `~/.config/systemd/user/docker.service.d`）。
2. 添加 `HTTP_PROXY` 或 `HTTPS_PROXY` 环境变量，可选设置 `NO_PROXY`（指定不需要经过代理的 Docker registries）。
   ```shell
   [Service]
   Environment="HTTP_PROXY=http://proxy.example.com:80"
   Environment="HTTPS_PROXY=https://proxy.example.com:443"
   Environment="NO_PROXY=localhost,127.0.0.1,docker-registry.example.com,.corp"
   ```
3. 使修改生效：
   ```shell
   systemctl --user daemon-reload
   systemctl --user restart docker
   ```

详细配置步骤参考官网：[Configure the daemon with systemd](https://docs.docker.com/config/daemon/systemd/#httphttps-proxy)。

在 `~/.docker/config.json` 配置的代理用于容器（即针对 Docker client），对 `docker pull`（Docker daemon）无效。

---

- [Stack Overflow - Cannot download Docker images behind a proxy](https://stackoverflow.com/questions/23111631/cannot-download-docker-images-behind-a-proxy)
- [Docker Docs - Configure the daemon with systemd](https://docs.docker.com/config/daemon/systemd/#httphttps-proxy)
- [Docker Docs - Configure Docker to use a proxy server](https://docs.docker.com/network/proxy/)
