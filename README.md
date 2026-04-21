# karpathy-codex

`karpathy-codex` 是一个给 Codex / ChatGPT 使用的 coding skill，用来约束实现节奏，强调先对齐需求、再确定最小设计、最后做小而准的代码改动。

本仓库推荐的安装方式是：

1. 先把仓库 clone 到用户主目录下的 `codex-skills/karpathy-codex`
2. 再把这个目录 link 到 Codex 的 skill 目录里

仓库地址：

[`https://github.com/beanqi/karpathy-codex.git`](https://github.com/beanqi/karpathy-codex.git)

## 安装前提

- 已安装 Git
- 已安装 Codex App，并且本地存在 Codex 配置目录

## macOS / Linux 安装

在终端里执行：

```bash
mkdir -p ~/codex-skills
git clone https://github.com/beanqi/karpathy-codex.git ~/codex-skills/karpathy-codex

mkdir -p ~/.codex/skills
ln -s ~/codex-skills/karpathy-codex ~/.codex/skills/karpathy-codex
```

安装完成后，目录关系大致如下：

```text
~/codex-skills/karpathy-codex
~/.codex/skills/karpathy-codex -> ~/codex-skills/karpathy-codex
```

如果之前已经装过旧版本，可以先删除旧的 link：

```bash
rm ~/.codex/skills/karpathy-codex
```

然后重新执行 `ln -s`。

## Windows 安装

推荐使用 PowerShell。

```powershell
New-Item -ItemType Directory -Force "$HOME\codex-skills" | Out-Null
git clone https://github.com/beanqi/karpathy-codex.git "$HOME\codex-skills\karpathy-codex"

New-Item -ItemType Directory -Force "$HOME\.codex\skills" | Out-Null
New-Item -ItemType Junction -Path "$HOME\.codex\skills\karpathy-codex" -Target "$HOME\codex-skills\karpathy-codex" | Out-Null
```

安装完成后，目录关系大致如下：

```text
%USERPROFILE%\codex-skills\karpathy-codex
%USERPROFILE%\.codex\skills\karpathy-codex -> %USERPROFILE%\codex-skills\karpathy-codex
```

如果之前已经装过旧版本，可以先删除旧的 link/junction：

```powershell
Remove-Item "$HOME\.codex\skills\karpathy-codex" -Force
```

然后重新执行 `New-Item -ItemType Junction ...`。

## 验证是否安装成功

确认以下文件路径存在即可：

- macOS / Linux: `~/.codex/skills/karpathy-codex/SKILL.md`
- Windows: `%USERPROFILE%\.codex\skills\karpathy-codex\SKILL.md`

如果 Codex App 已经在运行，安装后重启一下 App，通常会更稳妥。

## 更新这个 skill

后续更新时，只需要进入 clone 下来的仓库目录执行：

```bash
git -C ~/codex-skills/karpathy-codex pull
```

Windows PowerShell:

```powershell
git -C "$HOME\codex-skills\karpathy-codex" pull
```

因为 Codex 目录里放的是 link，所以不需要重复安装。
