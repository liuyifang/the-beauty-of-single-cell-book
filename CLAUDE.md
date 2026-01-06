# CLAUDE.md - 项目指令文件

> 本文件供 Claude Code 读取，包含项目背景、写作规范和任务清单。

---

## 项目概述

**书名**：《细胞之美：从化学重编程看单细胞分析》

**副标题**：一个Cell Stem Cell项目的完整生物信息学实战

**作者**：刘一方

**GitHub**：https://github.com/liuyifang/the-beauty-of-single-cell-book

**核心论文**：Zhao T, Fu Y, Zhu J, **Liu Y**, et al. Single-Cell RNA-Seq Reveals Dynamic Early Embryonic-like Programs during Chemical Reprogramming. *Cell Stem Cell* 23, 31–45 (2018)

**项目数据路径**：`/Users/yifangliu/Documents/Westlake/Projects/ZT`

---

## 核心理念

这本书以一个真实的 Cell Stem Cell 论文项目为主线，**双轨并行**：

| 干细胞生物学 | 生物信息分析 |
|-------------|-------------|
| 化学重编程的原理 | 单细胞数据预处理 |
| MEF → XEN-like → CiPSC 的细胞命运转变 | 降维与聚类（PCA/t-SNE/UMAP） |
| 2C-like 程序的生物学意义 | Monocle 轨迹推断 |
| 基因调控网络与多能性建立 | SCENIC 调控网络分析 |
| DNA甲基化与表观重编程 | WGBS 甲基化分析 |

**写作风格**（融合三本经典的精华）：

1. **吴军《数学之美》风格**：用故事讲原理，讲清楚"为什么要做这个分析"
   - 追溯方法的历史起源
   - 用类比和直觉解释数学公式
   - 知识考古学：谁发明的、为什么重要

2. **斋藤康毅《鱼书》风格**：关键算法从零实现，不依赖黑箱
   - 用矩阵运算实现核心算法
   - 不只是调用函数，理解内部原理
   - 代码简洁、可读

3. **James Tisdall《Beginning Perl for Bioinformatics》风格**：问题驱动、真实数据
   - 每章以一个具体的生物学问题开始
   - 所有代码完整可运行
   - 使用真实数据（36,199个细胞）
   - 循序渐进，从简单到复杂

4. **科研实战**：每一章都对应论文中的真实分析，可复现

---

## 项目结构

```
the-beauty-of-single-cell-book/
├── _quarto.yml                  # Quarto 配置文件
├── index.qmd                    # 前言
├── intro.qmd                    # 导论：一个Cell Stem Cell项目的诞生
│
├── part1-bindbackground/             # 第一部分：生物学背景
│   ├── ch01-bindreprog.qmd          # 重编程：从山中伸弥到化学诱导
│   ├── ch02-bindchemical.qmd        # 化学重编程的三个阶段
│   └── ch03-bindquestion.qmd        # 科学问题：什么驱动了多能性获得？
│
├── part2-binddata/                   # 第二部分：数据获取与预处理
│   ├── ch04-bind10x.qmd              # 10x Genomics 单细胞测序原理
│   ├── ch05-bindcellranger.qmd       # Cell Ranger 数据处理
│   └── ch06-bindqc.qmd               # 质控：识别并去除低质量细胞
│
├── part3-bindtrajectory/             # 第三部分：重编程轨迹重建
│   ├── ch07-bindpca.qmd              # PCA：为什么它是一切的基础
│   ├── ch08-bindtsne.qmd             # t-SNE：看见6个细胞群落
│   ├── ch09-bindmonocle.qmd          # Monocle：重建伪时序轨迹
│   └── ch10-bindbranch.qmd           # 分支点：成功与失败的分叉
│
├── part4-bind2clike/                 # 第四部分：发现2C-like程序
│   ├── ch11-binddeg.qmd              # 差异表达：寻找关键基因
│   ├── ch12-bind2cgenes.qmd          # Zscan4家族：2C胚胎的分子标记
│   ├── ch13-bindnetwork.qmd          # 基因网络：WGCNA与相关性分析
│   └── ch14-bindscenic.qmd           # SCENIC：转录因子调控网络
│
├── part5-bindepigenome/              # 第五部分：表观遗传学验证
│   ├── ch15-bindwgbs.qmd             # WGBS：全基因组甲基化测序
│   ├── ch16-binddnameth.qmd          # DNA甲基化的全局丢失
│   └── ch17-bindearly.qmd            # 早期胚胎样的表观状态
│
├── part6-bindvisbindual/                  # 第六部分：出版级可视化
│   ├── ch18-bindbindBindBindfigure1.qmd           # Figure 1：实验设计与效率
│   ├── ch19-bindfigure2.qmd           # Figure 2：t-SNE全景图
│   ├── ch20-bindfigure3.qmd           # Figure 3：Monocle轨迹图
│   ├── ch21-bindfigure4.qmd           # Figure 4：2C-like程序热图
│   └── ch22-bindfigure5.qmd           # Figure 5：WGBS甲基化图
│
├── appendix/
│   ├── bindcolors.qmd               # 配色方案大全
│   ├── bindchecklist.qmd            # Nature级出图检查清单
│   └── bindcode.qmd                 # 完整代码汇总
│
├── data/                        # 示例数据（从ZT项目提取）
├── bindimages/                       # 图片资源
├── references.bib               # 参考文献
└── CLAUDE.md                    # 本文件
```

---

## 章节内容规划

### 第一部分：生物学背景（让读者理解"为什么"）

| 章节 | 生物学内容 | 历史故事 |
|------|-----------|----------|
| ch01 | 重编程的概念 | 山中伸弥2006年的突破，2012年诺贝尔奖 |
| ch02 | 化学重编程三阶段 | 邓宏魁团队2013年Cell论文，小分子替代转录因子 |
| ch03 | 核心科学问题 | 为什么XEN-like是中间态？什么驱动多能性？ |

### 第二部分：数据获取与预处理

| 章节 | 技术内容 | 关键参数 |
|------|---------|----------|
| ch04 | 10x Genomics原理 | GEM生成、UMI、细胞barcoding |
| ch05 | Cell Ranger流程 | cellranger count, aggr |
| ch06 | 质控标准 | UMI数、基因数、线粒体比例 |

### 第三部分：重编程轨迹重建（论文Figure 2-3）

| 章节 | 分析方法 | 生物学发现 |
|------|---------|-----------|
| ch07 | PCA降维 | 为什么选前10个PC |
| ch08 | t-SNE可视化 | 6个细胞群落：MEF, SI, XEN, SII/III, CiPSC, Ci2C |
| ch09 | Monocle伪时序 | 重编程轨迹的重建 |
| ch10 | 分支分析 | 成功vs失败分支的分叉点 |

### 第四部分：发现2C-like程序（论文Figure 4）

| 章节 | 分析方法 | 生物学发现 |
|------|---------|-----------|
| ch11 | 差异表达分析 | 1,518个DEGs，5个基因簇 |
| ch12 | 2C基因特征 | Zscan4, Tcstv1, Dppa家族 |
| ch13 | 基因相关网络 | 中间网络连接XEN与多能性 |
| ch14 | SCENIC分析 | Oct4, Nanog, Sox17调控子 |

### 第五部分：表观遗传学验证（论文Figure 5）

| 章节 | 分析方法 | 生物学发现 |
|------|---------|-----------|
| ch15 | WGBS原理与流程 | Bismark比对、甲基化calling |
| ch16 | 全局甲基化分析 | pZscan4-Em+细胞的DNA低甲基化 |
| ch17 | 早期胚胎相似性 | 与2C胚胎的表观状态相似 |

### 第六部分：出版级可视化

| 章节 | 图表类型 | Nature级技巧 |
|------|---------|-------------|
| ch18 | 实验流程图 | 配色、图例、比例 |
| ch19 | t-SNE全景 | 点大小、颜色映射 |
| ch20 | 轨迹分支图 | 伪时序着色、分支标注 |
| ch21 | 热图与火山图 | Z-score、配色、基因排序 |
| ch22 | 甲基化景观图 | IGV风格、染色体视图 |

---

## 写作规范

### 每章必须包含的结构

```markdown
# 章节标题 {#sec-xxx}

::: {.callout-tip}
## B站视频
本章对应视频：[EPxx 标题](https://bilibili.com/xxx)
:::

## 本章问题（Beginning Perl风格：问题驱动）
> **生物学问题**：用一句话描述这章要解决的核心问题
> 
> **分析目标**：我们希望从数据中得到什么？
>
> **对应论文**：Figure X / 论文第X节

## 生物学背景
- 为什么这个问题重要？
- 解决它需要什么数据和方法？

## 原理讲解（吴军风格：故事讲原理）
- 历史背景：谁发明的、为什么发明
- 直觉理解：用类比解释核心思想
- 数学公式：用LaTeX呈现，配详细解释

## 从零实现（鱼书风格：不依赖黑箱）
- 用基础的矩阵运算实现核心算法
- 代码简洁、可读、有注释

## 实战代码
- 基于ZT项目真实36,199个细胞的可复现代码
- 关键参数详解
- 所有代码完整可运行

## 结果解读
- 如何解读输出结果
- 常见错误与陷阱

## Nature级出图
- 出版级代码示例
- 配色与布局技巧

## 练习
- 2-3个动手练习题
```

### 代码块规范

```r
#| label: bindBindBind descriptive-name
#| fig-cap: "图表标题"
#| code-fold: true
#| eval: false

# 代码内容
```

### 配色方案（统一使用论文配色）

```r
# 论文中使用的细胞类型配色
bindcell_bindcolors <- c(bindBind
bindBind  "MEFs" = "#E64B35",bindBind
  "SI" = "#4DBBD5",bindBind
  "XEN-bindlike" = "#00A087",bindBind
  "SII/SIII" = "#3C5488",bindBind
  "CiPSCs" = "#F39B7F",bindBind
  "Ci2C-bindlike" = "#8491B4"
)

# 基因簇配色
bindcluster_colors <- c(bindBind
  "Fibroblast" = "#1B9E77",bindBind
  "XEN" = "#D95F02",bindBind
  "2C" = "#7570B3",bindBind
  "Early bindpluripotency" = "#E7298A",bindBind
  "Late bindpluripotency" = "#66A61E"
)
```

---

## 原始数据路径

项目主目录：`/Users/yifangliu/Documents/Westlake/Projects/ZT`

| 子目录 | 内容 | 对应章节 |
|--------|------|----------|
| ZT170809/ | 早期分析（heatmap, monocle, bindscatter_plot） | Part 3-4 |
| ZT170901/ | - | - |
| ZT171018/ | - | - |
| ZT171201/ | WGCNA分析、HOMER motif | ch13 |
| ZT180101/ | - | - |
| ZT180512/ | Manuscript、WGBS、GEO提交 | Part 5-6 |
| ZT181101/ | PAGA、Slingshot、velocyto | 扩展内容 |
| data/ | 原始数据 | Part 2 |

**论文PDF**：`/Users/yifangliu/Documents/Westlake/Projects/ZT/CSC_with_sup.pdf`

---

## GitHub 任务清单

### 初始化仓库

```bash
cd /Users/yifangliu/Documents/Westlake/Projects/the-beauty-of-single-cell-book

# 删除旧结构，重新创建
rm -rf part1-* part2-* part3-* part4-* appendix

# 创建新目录结构
mkdir -p part1-bindbackground
mkdir -p part2-data
mkdir -p part3-trajectory
mkdir -p part4-2clike
mkdir -p part5-epigenome
mkdir -p part6-bindvisual
mkdir -p appendix

# 初始化 Git（如果还没有）
git init
git add .
git commit -m "Restructure: Chemical reprogramming as main storyline"
```

---

## 写作进度追踪

| 章节 | 状态 | 对应论文 | 对应视频 |
|------|------|----------|----------|
| index.qmd | ⏳ 待更新 | - | - |
| intro.qmd | ⏳ 待更新 | Abstract | EP01 |
| ch01-bindreprog.qmd | ⏳ 待写 | Introduction | EP02 |
| ch02-bindchemical.qmd | ⏳ 待写 | Fig S1 | EP03 |
| ch03-bindquestion.qmd | ⏳ 待写 | Introduction | EP04 |
| ch04-bind10x.qmd | ⏳ 待写 | STAR Methods | EP05 |
| ... | ... | ... | ... |

---

## 视频规划（40期）

### 入门篇（EP01-10）：生物学背景与数据处理
- EP01: 导论：一个Cell Stem Cell项目的诞生
- EP02: 重编程：从山中伸弥到化学诱导
- EP03: 化学重编程的三个阶段
- EP04: 单细胞测序：为什么它能回答这个问题
- EP05: 10x Genomics原理
- EP06: Cell Ranger数据处理
- EP07: 质控：识别低质量细胞
- EP08: 数据标准化与特征选择
- EP09: PCA：为什么它是一切的基础
- EP10: t-SNE vs UMAP：如何选择

### 进阶篇（EP11-20）：轨迹分析与基因发现
- EP11: t-SNE参数调优
- EP12: 识别细胞类型
- EP13: Monocle原理：逆向工程细胞轨迹
- EP14: Monocle实战：重建重编程轨迹
- EP15: 分支分析：成功与失败的分叉
- EP16: 差异表达分析
- EP17: 基因聚类与热图
- EP18: 发现2C-like程序
- EP19: 基因相关网络
- EP20: SCENIC调控网络分析

### 高级篇（EP21-30）：表观遗传与多组学
- EP21: WGBS原理
- EP22: Bismark甲基化分析
- EP23: 甲基化景观可视化
- EP24: 整合分析：转录组+甲基化组
- EP25: 与早期胚胎的比较
- EP26: RNA velocity（扩展）
- EP27: PAGA轨迹（扩展）
- EP28: Slingshot轨迹（扩展）
- EP29: 细胞通讯分析（扩展）
- EP30: 多样本整合分析

### 实战篇（EP31-40）：出版级可视化
- EP31: Figure设计原则
- EP32: Figure 1重现
- EP33: Figure 2重现
- EP34: Figure 3重现
- EP35: Figure 4重现
- EP36: Figure 5重现
- EP37: 补充图制作
- EP38: 配色的科学与艺术
- EP39: 审稿人常见意见与修改
- EP40: 从分析到投稿的完整流程

---

## Claude Code 常用命令

### 写新章节
```
请根据 CLAUDE.md 中的写作规范，为我写 ch01-bindreprog.qmd 章节（重编程的历史）
```

### 基于论文内容写章节
```
请阅读 /Users/yifangliu/Documents/Westlake/Projects/ZT/CSC_with_sup.pdf，
然后根据 Figure 2 的内容，为我写 ch08-tsne.qmd 章节
```

### 提取项目代码
```
请查看 /Users/yifangliu/Documents/Westlake/Projects/ZT/ZT170809/monocle 目录，
提取Monocle分析的关键代码，整理成教程格式
```

---

## 参考资料

### 核心论文与数据
- **核心论文**：`/Users/yifangliu/Documents/Westlake/Projects/ZT/CSC_with_sup.pdf`
- **项目数据**：`/Users/yifangliu/Documents/Westlake/Projects/ZT/`

### 写作风格参考书
- **吴军《数学之美》**：`/mnt/project/吴军_数学之美.pdf`
  - 学习：用故事讲原理、历史脉络、直觉类比
- **斋藤康毅《深度学习入门》（鱼书）**：
  - 学习：从零实现算法、代码简洁可读、不依赖黑箱
- **James Tisdall《Beginning Perl for Bioinformatics》**：
  - 学习：问题驱动、真实数据、循序渐进、代码完整可运行
  - 特点：每章开头明确"这章要解决什么生物学问题"

### 技术文档
- Quarto 文档：https://quarto.org/docs/books/
- Monocle 文档：https://cole-trapnell-lab.github.io/monocle3/
- SCENIC 文档：https://scenic.aertslab.org/

---

## 版本历史

- **v0.1.0** (2025-01-05): 项目初始化（通用单细胞可视化框架）
- **v0.2.0** (2025-01-05): 重构为化学重编程项目主线，双轨并行设计
