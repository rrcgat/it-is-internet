# Docker

## 设置镜像源加速 `docker pull`

### Linux/macOS

1. 修改 `daemon.json`，Linux 下位于 `/etc/docker/` 目录下，macOS 中使用 Docker Desktop 修改。
2. 在最外层加上 `registry-mirrors` 作为键，值为数组，数组中的每个元素都是一个镜像源。
3. 重启 Docker。

例如：

```json
{
 "registry-mirrors" : [
   "https://mirror.ccs.tencentyun.com"
 ]
}
```

### 可用镜像源

- https://hub-mirror.c.163.com
- https://dockerhub.azk8s.cn
- https://mirror.ccs.tencentyun.com
