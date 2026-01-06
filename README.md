# 细胞之美：从化学重编程看单细胞分析

[![Quarto Publish](https://github.com/liuyifang/the-beauty-of-single-cell-book/actions/workflows/publish.yml/badge.svg)](https://github.com/liuyifang/the-beauty-of-single-cell-book/actions/workflows/publish.yml)

> 一个 Cell Stem Cell 项目的完整生物信息学实战

## 📖 在线阅读

**电子书地址**：[https://liuyifang.github.io/the-beauty-of-single-cell-book](https://liuyifang.github.io/the-beauty-of-single-cell-book)

## 🎬 配套视频

**B站系列**：搜索"细胞之美"或访问 [作者主页](https://space.bilibili.com/xxx)

## 📚 本书特色

### 以真实项目为主线

整本书围绕一篇 **Cell Stem Cell 2018** 论文展开：

> Zhao T, Fu Y, Zhu J, **Liu Y**, et al. Single-Cell RNA-Seq Reveals Dynamic Early Embryonic-like Programs during Chemical Reprogramming. *Cell Stem Cell* 23, 31–45 (2018)

你将看到36,199个真实细胞在化学重编程过程中的命运变化。

### 双轨并行

| 干细胞生物学 | 生物信息分析 |
|-------------|-------------|
| 化学重编程的原理 | 单细胞数据预处理 |
| MEF → XEN-like → CiPSC | t-SNE/UMAP聚类 |
| 2C-like程序的发现 | Monocle轨迹推断 |
| DNA甲基化重编程 | WGBS分析 |

### 写作风格

- **吴军《数学之美》风格**：用故事讲原理
- **斋藤康毅《鱼书》风格**：关键算法从零实现

## 📋 目录

### 第一部分：生物学背景
- [ ] 第1章：重编程——从山中伸弥到化学诱导
- [ ] 第2章：化学重编程的三个阶段
- [ ] 第3章：科学问题——什么驱动了多能性获得？

### 第二部分：数据获取与预处理
- [ ] 第4章：10x Genomics单细胞测序原理
- [ ] 第5章：Cell Ranger数据处理
- [ ] 第6章：质控——识别并去除低质量细胞

### 第三部分：重编程轨迹重建
- [ ] 第7章：PCA——为什么它是一切的基础
- [ ] 第8章：t-SNE——看见6个细胞群落
- [ ] 第9章：Monocle——重建伪时序轨迹
- [ ] 第10章：分支点——成功与失败的分叉

### 第四部分：发现2C-like程序
- [ ] 第11章：差异表达——寻找关键基因
- [ ] 第12章：Zscan4家族——2C胚胎的分子标记
- [ ] 第13章：基因网络——WGCNA与相关性分析
- [ ] 第14章：SCENIC——转录因子调控网络

### 第五部分：表观遗传学验证
- [ ] 第15章：WGBS——全基因组甲基化测序
- [ ] 第16章：DNA甲基化的全局丢失
- [ ] 第17章：早期胚胎样的表观状态

### 第六部分：出版级可视化
- [ ] 第18-22章：论文Figure 1-5的完整重现

### 附录
- [ ] 附录A：配色方案大全
- [ ] 附录B：Nature出图检查清单
- [ ] 附录C：完整代码汇总

## 🛠️ 本地构建

```bash
git clone https://github.com/liuyifang/the-beauty-of-single-cell-book.git
cd the-beauty-of-single-cell-book
quarto preview
```

## 📝 参与贡献

欢迎提交 Issue 和 Pull Request！

## 📜 许可证

- 内容：[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)
- 代码：MIT License

## 👤 作者

**刘一方** - Cell Stem Cell 2018 共同第一作者

- GitHub: [@liuyifang](https://github.com/liuyifang)

---

⭐ 如果这本书对你有帮助，请给个 Star！
