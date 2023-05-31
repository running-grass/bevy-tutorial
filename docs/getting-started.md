---
sidebar_position: 2
---

# 入门指南

本节将帮助您尽快开始使用 Bevy。它将引导您设置开发环境并编写一个简单的 Bevy 应用程序。

## 快速入门
如果您希望立即开始，并且已经有一个可用的 Rust 设置，请随时按照这个 "快速入门" 指南进行操作。否则，请继续下一页。

注意：关于 "快速编译" 设置的说明在下一页，所以您可能希望先阅读该部分。

### 尝试示例

1. 克隆 Bevy 仓库：

```bash
git clone https://github.com/bevyengine/bevy
```

2. 导航到新的 "bevy" 文件夹：
```bash
cd bevy
```

3. 切换到正确的 Bevy 版本（默认情况下是 git 的主开发分支）：

```bash
# 使用最新的 Bevy 发行版
git checkout latest

# 或者指定版本
git checkout v0.10.0
```

4. 尝试 examples 文件夹中的示例：

```bash
cargo run --example breakout
```

### 将 Bevy 添加为依赖项
Bevy 可以作为 crates.io 上的库使用。

将其添加到您的项目最简单的方法是使用 `cargo add` ：

```bash
cargo add bevy
```

或者，您可以手动将其添加到项目的 `Cargo.toml` 文件中，如下所示：

```toml
[dependencies]
bevy = "0.11" # 确保这是最新版本
```

确保使用最新的 bevy crate 版本（Crates.io）。