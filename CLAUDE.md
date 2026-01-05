# CLAUDE.md - 项目指令文件

> 本文件供 Claude Code 读取，包含项目背景、写作规范和任务清单。

---

## 项目概述

**书名**：《细胞之美：R语言单细胞可视化从原理到实践》

**作者**：刘一方

**GitHub**：https://github.com/liuyifang/scviz-book

**定位**：面向生物信息学研究者的单细胞可视化教程，配套B站视频系列

**核心理念**：
1. **吴军《数学之美》风格**：用故事讲原理，用历史讲脉络
2. **斋藤康毅《鱼书》风格**：从零实现，不依赖黑箱
3. **科研品味**：不只是"怎么画"，更是"为什么选这种图"和"怎样画成Nature级别"

---

## 项目结构

```
scviz-book/
├── .github/
│   └── workflows/
│       └── publish.yml          # GitHub Actions 自动部署
├── _quarto.yml                  # Quarto 配置文件
├── index.qmd                    # 前言
├── intro.qmd                    # 导论
├── part1-dimred/                # 第一部分：降维与散点图
│   ├── ch01-pca.qmd            # ✅ 已完成
│   ├── ch02-umap.qmd           # ✅ 已完成
│   └── ch03-tsne.qmd           # 待写
├── part2-expression/            # 第二部分：表达量可视化
│   ├── ch04-featureplot.qmd    # 待写
│   ├── ch05-dotplot.qmd        # 待写
│   ├── ch06-heatmap.qmd        # 待写
│   └── ch07-violin.qmd         # 待写
├── part3-trajectory/            # 第三部分：轨迹与动态
│   ├── ch08-monocle.qmd        # 待写
│   ├── ch09-velocity.qmd       # 待写
│   └── ch10-cytotrace.qmd      # 待写
├── part4-comm/                  # 第四部分：细胞通讯
│   ├── ch11-cellchat.qmd       # 待写
│   └── ch12-commot.qmd         # 待写
├── appendix/                    # 附录
│   ├── colors.qmd              # 配色方案大全
│   └── checklist.qmd           # Nature出图检查清单
├── data/                        # 示例数据
├── images/                      # 图片资源
├── references.bib               # 参考文献
├── nature.csl                   # Nature引用格式
├── README.md                    # GitHub首页说明
├── LICENSE                      # 许可证
└── CLAUDE.md                    # 本文件
```

---

## 写作规范

### 每章必须包含的结构

```markdown
# 章节标题 {#sec-xxx}

::: {.callout-tip}
## B站视频
本章对应视频：[EPxx 标题](https://bilibili.com/xxx)
:::

## 科研品味：什么时候用它？
- 应该用的场景
- 不应该用的场景
- 审稿人期待什么

## 数学原理
- 直觉理解（类比、故事）
- 历史背景（谁发明的、为什么）
- 数学公式（LaTeX格式）

## 从零实现
- 不调用现成函数
- 用矩阵运算实现核心算法
- 代码折叠：code-fold: true

## Seurat/Scanpy 标准流程
- 常用参数详解
- 常见错误示范

## Nature级出图
- 完整代码示例
- 配色方案
- 出版级checklist

## 常见问题
- Q&A格式

## 练习
- 2-3个动手练习

---
**下一章：** [链接](path/to/next.qmd)
```

### 代码块规范

```r
#| label: descriptive-name
#| fig-cap: "图表标题"
#| code-fold: true
#| eval: false

# 代码内容
```

### 配色方案（统一使用）

```r
# Nature风格配色
nature_colors <- c(
  "#E64B35", "#4DBBD5", "#00A087", "#3C5488",
  "#F39B7F", "#8491B4", "#91D1C2", "#DC0000",
  "#7E6148", "#B09C85"
)

# 连续型配色
viridis_colors <- viridis::viridis(100)
```

### 数学公式格式

- 行内公式：`$x^2$`
- 独立公式：`$$\sum_{i=1}^n x_i$$`
- 对齐公式使用 `aligned` 环境

---

## 章节内容规划

### 第一部分：降维与散点图

| 章节 | 核心内容 | 数学原理 | 历史故事 |
|------|----------|----------|----------|
| ch01-pca | 主成分分析 | 特征值分解 | Karl Pearson 1901 |
| ch02-umap | UMAP降维 | 拓扑数据分析 | McInnes 2018 |
| ch03-tsne | t-SNE对比 | KL散度 | van der Maaten 2008 |

### 第二部分：表达量可视化

| 章节 | 核心内容 | 关键参数 | 常见错误 |
|------|----------|----------|----------|
| ch04-featureplot | 空间表达分布 | 配色选择 | 彩虹色阶 |
| ch05-dotplot | 双编码展示 | 点大小vs颜色 | 基因顺序混乱 |
| ch06-heatmap | 表达矩阵热图 | Z-score标准化 | 未聚类 |
| ch07-violin | 分布展示 | 核密度估计 | 与boxplot混淆 |

### 第三部分：轨迹与动态

| 章节 | 核心内容 | 工具 | 输出图类型 |
|------|----------|------|------------|
| ch08-monocle | 拟时序分析 | Monocle3 | 轨迹图+拟时序热图 |
| ch09-velocity | RNA速度 | scVelo | 速度流向图 |
| ch10-cytotrace | 分化潜能 | CytoTRACE2 | 潜能评分图 |

### 第四部分：细胞通讯

| 章节 | 核心内容 | 工具 | 输出图类型 |
|------|----------|------|------------|
| ch11-cellchat | 配受体通讯 | CellChat | 圈图+气泡图 |
| ch12-commot | 空间通讯 | COMMOT | 空间流向图 |

---

## GitHub 任务清单

### 初始化仓库（待执行）

```bash
cd /Users/yifangliu/Documents/Playground/scviz-book

# 初始化 Git
git init

# 创建 .gitignore
cat > .gitignore << 'EOF'
# Quarto
/.quarto/
/_site/
/docs/

# R
.Rproj.user
.Rhistory
.RData
.Ruserdata
*.Rproj

# macOS
.DS_Store

# Data files (too large)
data/*.rds
data/*.h5ad
data/*.h5

# Rendered output
_freeze/
EOF

# 添加所有文件
git add .

# 首次提交
git commit -m "Initial commit: project structure and first chapters"

# 连接远程仓库（需先在GitHub创建空仓库scviz-book）
git remote add origin https://github.com/liuyifang/scviz-book.git

# 推送
git branch -M main
git push -u origin main
```

### 创建 GitHub Actions 自动部署

文件：`.github/workflows/publish.yml`

```yaml
name: Publish Book

on:
  push:
    branches: [main]
  workflow_dispatch:

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    permissions:
      contents: write
      pages: write
    
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      
      - name: Setup R
        uses: r-lib/actions/setup-r@v2
        with:
          r-version: '4.3.0'
      
      - name: Setup R dependencies
        uses: r-lib/actions/setup-r-dependencies@v2
        with:
          packages: |
            any::knitr
            any::rmarkdown
            any::ggplot2
            any::dplyr
      
      - name: Setup Quarto
        uses: quarto-dev/quarto-actions/setup@v2
        
      - name: Render Book
        run: quarto render
        
      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./docs
```

### 启用 GitHub Pages

1. 进入仓库 Settings → Pages
2. Source 选择 "Deploy from a branch"
3. Branch 选择 "gh-pages" / root
4. 保存

---

## 待创建的占位文件

以下文件需要创建占位内容，让 Quarto 能正常编译：

- [ ] `part1-dimred/ch03-tsne.qmd`
- [ ] `part2-expression/ch04-featureplot.qmd`
- [ ] `part2-expression/ch05-dotplot.qmd`
- [ ] `part2-expression/ch06-heatmap.qmd`
- [ ] `part2-expression/ch07-violin.qmd`
- [ ] `part3-trajectory/ch08-monocle.qmd`
- [ ] `part3-trajectory/ch09-velocity.qmd`
- [ ] `part3-trajectory/ch10-cytotrace.qmd`
- [ ] `part4-comm/ch11-cellchat.qmd`
- [ ] `part4-comm/ch12-commot.qmd`
- [ ] `appendix/colors.qmd`
- [ ] `appendix/checklist.qmd`
- [ ] `references.qmd`
- [ ] `references.bib`
- [ ] `README.md`
- [ ] `LICENSE`

---

## 写作进度追踪

| 章节 | 状态 | 对应视频 | 完成日期 |
|------|------|----------|----------|
| index.qmd | ✅ 完成 | - | 2025-01-05 |
| intro.qmd | ✅ 完成 | EP01 | 2025-01-05 |
| ch01-pca.qmd | ✅ 完成 | EP02 | 2025-01-05 |
| ch02-umap.qmd | ✅ 完成 | EP03 | 2025-01-05 |
| ch03-tsne.qmd | ⏳ 待写 | EP04 | - |
| ch04-featureplot.qmd | ⏳ 待写 | EP05 | - |
| ... | ... | ... | - |

---

## Claude Code 常用命令

### 写新章节
```
请根据 CLAUDE.md 中的写作规范，为我写 ch03-tsne.qmd 章节
```

### 检查并修复格式
```
检查 part1-dimred/ 下所有 .qmd 文件是否符合 CLAUDE.md 中的写作规范
```

### 创建占位文件
```
为 _quarto.yml 中列出的所有章节创建占位文件
```

### 预览书籍
```bash
cd /Users/yifangliu/Documents/Playground/scviz-book
quarto preview
```

### 构建书籍
```bash
quarto render
```

### 推送更新
```bash
git add .
git commit -m "Update: 章节描述"
git push
```

---

## 参考资料

- 作者项目数据：`/Users/yifangliu/Documents/Westlake/Projects/JiabinChen/Embryo_JiabinChen`
- Quarto 文档：https://quarto.org/docs/books/
- Seurat 文档：https://satijalab.org/seurat/
- 《数学之美》写作风格参考
- 《深度学习入门》代码风格参考

---

## 版本历史

- **v0.1.0** (2025-01-05): 项目初始化，完成前4个文件
- **v0.2.0** (待定): 完成第一部分全部章节
- **v0.3.0** (待定): 完成第二部分全部章节
- **v1.0.0** (待定): 全书完成，正式发布
