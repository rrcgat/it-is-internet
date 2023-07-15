# Rust

## Rust Crates

编辑 `$CARGO_HOME/config` 文件，加入镜像源，Cargo 1.68 开始可使用稀疏索引

清华镜像源：

```
[source.crates-io]
replace-with = 'mirror'

[source.mirror]
registry = "sparse+https://mirrors.tuna.tsinghua.edu.cn/crates.io-index/"
```

中科大镜像源：

```
[source.crates-io]
replace-with = 'ustc'

[source.ustc]
registry = "sparse+https://mirrors.ustc.edu.cn/crates.io-index/"
```

[tuna - Rust crates.io 稀疏索引镜像使用帮助](https://mirrors.tuna.tsinghua.edu.cn/help/crates.io-index/)
[ustc - Rust Crates 源使用帮助](https://mirrors.ustc.edu.cn/help/crates.io-index.html)
