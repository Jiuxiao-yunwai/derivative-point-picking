<div align="center">

# 导数取点.skill

> *"不是不会算，是不能只写趋于无穷。"*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Codex Skill](https://img.shields.io/badge/Codex-Skill-blueviolet)](SKILL.md)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blueviolet)](https://docs.claude.com/en/docs/claude-code/skills)
[![OpenClaw](https://img.shields.io/badge/OpenClaw-Compatible-111827)](https://docs.openclaw.ai/tools/skills)
[![AgentSkills](https://img.shields.io/badge/AgentSkills-Compatible-green)](https://www.agentskills.in/docs/getting-started)
[![Math](https://img.shields.io/badge/Math-Derivative-blue.svg)](SKILL.md)
[![Gaokao](https://img.shields.io/badge/Gaokao-Proof-green.svg)](SKILL.md)
[![Language](https://img.shields.io/badge/Language-中文-red.svg)](README.md)

<br>

AI 会用极限猜答案，<br>
但高考阅卷要的是能落在纸上的证明。<br>
AI 会说“显然存在”，<br>
但学生真正需要知道：这个点为什么这么取？<br>

**先用极限和单调性探路，再用取点和零点存在定理收束。**

<br>

面向导数压轴题、函数零点、参数范围、存在性证明<br>
把“趋于”“显然”“值域可得”改写成**具体取点 + 连续性 + 阅卷友好证明**<br>
让 AI 不只给答案，也讲清楚取点从哪里来

[为什么需要](#为什么需要这个-skill) · [能力范围](#能力范围) · [安装](#安装) · [使用](#使用方式) · [例子](#例子) · [核心规则](#skill-的核心规则)

</div>

---

## 能力范围

| 场景 | 分析方式 | 最终写法 | 重点 |
|------|:-------:|:-------:|------|
| 零点存在 | 单调性、极值、极限 | 取点异号 + 零点存在定理 | 不只写“趋于” |
| 参数范围 | 必要性、充分性 | 分两步证明 | 端点必须检查 |
| 导数压轴题 | 函数构造、放缩 | 取点来源说明 | 点不能凭空出现 |
| 指数对数混合 | 切线放缩、同构换元 | 简化后反推取点 | 解释为什么这样取 |
| 恒成立问题 | 最值、切线、二次拟合 | 转化为不等式证明 | 保留阅卷链条 |
| 数列极限夹逼 | 极限探路 | 显式取足够大的 \(n\) | 避免只靠极限语言 |

## 为什么需要这个 Skill

很多 AI 在解导数题时，会这样写：

> 因为函数连续，且两端趋于正无穷，所以值域为某个区间。

这种写法在数学上可能能说通，但在高考解答中，尤其是证明“存在某个点”时，不一定足够稳妥。

更适合阅卷的写法通常是：

1. 先用极限、单调性、值域思想分析出答案；
2. 再把存在性证明改写为“取一个具体点，使函数值异号”；
3. 最后用零点存在定理或介值定理完成证明。

这个 Skill 就是把这种解题习惯固定下来。

## 安装

仓库地址：

```text
https://github.com/Jiuxiao-yunwai/derivative-point-picking
```

### Codex

```powershell
git clone https://github.com/Jiuxiao-yunwai/derivative-point-picking.git C:\Users\你的用户名\.codex\skills\derivative-point-picking
```

如果你已经把仓库下载到本地，也可以直接把整个文件夹复制到：

```text
C:\Users\你的用户名\.codex\skills\derivative-point-picking
```

### Claude Code

个人 Skill，所有项目可用：

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/Jiuxiao-yunwai/derivative-point-picking.git ~/.claude/skills/derivative-point-picking
```

项目 Skill，只在当前项目可用：

```bash
mkdir -p .claude/skills
git clone https://github.com/Jiuxiao-yunwai/derivative-point-picking.git .claude/skills/derivative-point-picking
```

Windows PowerShell 也可以使用：

```powershell
git clone https://github.com/Jiuxiao-yunwai/derivative-point-picking.git $env:USERPROFILE\.claude\skills\derivative-point-picking
```

### Claude.ai

Claude.ai 的自定义 Skill 通常使用 ZIP 上传：

1. 下载或克隆本仓库；
2. 确保 ZIP 内包含 `derivative-point-picking/` 文件夹，而不是把 `SKILL.md` 直接放在 ZIP 根目录；
3. 在 Claude.ai 中进入 `Customize > Skills`；
4. 选择创建/上传 Skill，并上传 ZIP 文件。

### OpenClaw

OpenClaw 支持 AgentSkills 兼容的 Skill 文件夹。常用安装位置如下：

工作区 Skill：

```bash
mkdir -p skills
git clone https://github.com/Jiuxiao-yunwai/derivative-point-picking.git skills/derivative-point-picking
```

项目 Agent Skill：

```bash
mkdir -p .agents/skills
git clone https://github.com/Jiuxiao-yunwai/derivative-point-picking.git .agents/skills/derivative-point-picking
```

个人 Agent Skill：

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/Jiuxiao-yunwai/derivative-point-picking.git ~/.agents/skills/derivative-point-picking
```

如果之后发布到 ClawHub，也可以使用：

```bash
openclaw skills install derivative-point-picking
```

### AgentSkills CLI

如果你使用 AgentSkills CLI：

```bash
npm install -g agent-skills-cli
skills add Jiuxiao-yunwai/derivative-point-picking
```

## 使用方式

使用时可以这样说：

```text
用 $derivative-point-picking 解这道导数题，注意讲清楚取点来源。
```

或：

```text
用 $derivative-point-picking 把这道题改写成高考阅卷友好的证明。
```

## 例子

题目：

已知 \(a,b\in\mathbb R\)，函数

\[
f(x)=e^x-a\sin x,\qquad g(x)=b\sqrt{x}.
\]

若曲线 \(y=f(x)\) 和 \(y=g(x)\) 有公共点，当 \(a=0\) 时，求 \(b\) 的取值范围。

### 普通分析

当 \(a=0\) 时，公共点条件为

\[
e^x=b\sqrt{x}.
\]

因为 \(x=0\) 时左边为 \(1\)，右边为 \(0\)，所以公共点必须满足 \(x>0\)。

于是

\[
b=\frac{e^x}{\sqrt{x}}.
\]

设

\[
\varphi(x)=\frac{e^x}{\sqrt{x}},\qquad x>0.
\]

求导可得

\[
\varphi'(x)=\frac{e^x}{x\sqrt{x}}\left(x-\frac12\right).
\]

所以 \(\varphi(x)\) 在 \((0,\frac12)\) 上单调递减，在 \((\frac12,+\infty)\) 上单调递增，最小值为

\[
\varphi\left(\frac12\right)=\sqrt{2e}.
\]

因此必要性为

\[
b\ge \sqrt{2e}.
\]

但如果只写“\(\varphi(x)\to+\infty\)，所以值域为 \([\sqrt{2e},+\infty)\)”作为充分性，在高考书写中可能不够稳。

### 取点式证明

下面证明：当 \(b\ge\sqrt{2e}\) 时，确实存在 \(x>0\)，使

\[
\frac{e^x}{\sqrt{x}}=b.
\]

令

\[
h(x)=\frac{e^x}{\sqrt{x}}-b,\qquad x>0.
\]

由前面的单调性可知，\(h(x)\) 在 \(x=\frac12\) 处取最小值，且

\[
h\left(\frac12\right)=\sqrt{2e}-b\le 0.
\]

接下来需要找一个点，使 \(h(x)>0\)。

取点不是凭空来的。我们希望

\[
\frac{e^x}{\sqrt{x}}>b.
\]

如果先让 \(\sqrt{x}=\frac1b\)，即

\[
x=\frac1{b^2},
\]

那么

\[
\frac{e^x}{\sqrt{x}}
=be^{1/b^2}>b.
\]

这就是取

\[
x=\frac1{b^2}
\]

的来源。

又因为 \(b\ge\sqrt{2e}\)，所以

\[
\frac1{b^2}\le\frac1{2e}<\frac12.
\]

于是

\[
h\left(\frac1{b^2}\right)
=be^{1/b^2}-b
=b\left(e^{1/b^2}-1\right)>0,
\]

而

\[
h\left(\frac12\right)\le0.
\]

由连续函数零点存在定理，\(h(x)\) 在区间

\[
\left(\frac1{b^2},\frac12\right]
\]

内存在零点，即存在 \(x_0>0\)，使

\[
h(x_0)=0.
\]

因此

\[
e^{x_0}=b\sqrt{x_0},
\]

两曲线有公共点。

综上，

\[
\boxed{b\in[\sqrt{2e},+\infty)}.
\]

## Skill 的核心规则

这个 Skill 会尽量遵循以下原则：

- 可以用极限、图像、单调性先分析答案；
- 最终证明存在性时，优先使用具体取点；
- 取点必须解释来源，不能像“魔法点”一样突然出现；
- 参数范围题必须分必要性和充分性；
- 数列中的极限夹逼，尽量改写为显式取足够大的 \(n\)；
- 对学生讲解时，说明放缩、切线、泰勒估计、同构换元等取点依据。

## 适用题型

- 导数压轴题；
- 零点个数问题；
- 参数取值范围；
- 恒成立与存在性问题；
- 指数、对数、三角函数混合问题；
- 需要用取点证明充分性的高考题；
- AI 解答中出现“趋于”“显然存在”“值域显然为”但证明不够稳的题目。
