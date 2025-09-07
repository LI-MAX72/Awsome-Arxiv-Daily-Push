# arXiv 每日论文提取脚本

这是一个 Python 脚本，可以自动提取 arXiv 上每日更新的论文，并将其信息（标题、作者、摘要、链接等）保存在一个 CSV 文件中。您可以轻松指定一个或多个自己感兴趣的研究领域，并可选择性地加入关键词进行过滤。

## 功能

- 可以按一个或多个指定的研究领域（如 `cs.AI`、`stat.ML` 等）进行搜索。
- **新增功能**：可以指定一个或多个关键词，只提取标题或摘要中包含这些关键词的论文。
- 自动获取前一天发布的最新论文。
- 将所有指定领域的论文合并到一个文件中，并自动去除重复的论文（因为一篇论文可能属于多个领域）。
- 提取论文的标题、作者、发布日期、摘要、arXiv 链接和 PDF 链接。
- 将所有信息整理并存储到一个 CSV 文件中，方便用 Excel 或其他工具打开和筛选。

## 如何使用

### 1. 环境准备

首先，您需要安装 Python。然后，在您的终端（命令行）中安装此脚本所需的库。

```
pip install arxiv pandas
```

- `arxiv`: 一个方便调用 arXiv API 的 Python 库。
- `pandas`: 一个强大的数据处理库，我们用它来生成 CSV 文件。

### 2. 配置搜索条件

打开 `arxiv_daily_fetcher.py` 脚本文件，找到文件底部的配置部分。

#### a. 配置研究领域 (必须)

找到这部分代码，修改为您感兴趣的领域组合。

```
# --- 1. 请在这里修改您想关注的一个或多个研究领域 ---
SEARCH_CATEGORIES = ['cs.AI', 'cs.CV', 'stat.ML']
```

#### b. 配置关键词 (可选)

在紧接着的下方，您可以添加希望在标题或摘要中搜索的关键词。

```
# --- 2. (可选) 请在这里添加您想搜索的关键词 ---
# 如果列表为空，则不进行关键词过滤
SEARCH_KEYWORDS = ["transformer", "diffusion model"]
```

- **如果需要关键词过滤**：在列表中填入您想搜索的词，例如 `["transformer", "attention"]`。
- **如果不需要关键词过滤**：将列表留空，像这样：`SEARCH_KEYWORDS = []`。

**一些常见的研究领域代码：**

| **代码**  | **领域**                              |
| --------- | ------------------------------------- |
| `cs.AI`   | 人工智能 (Artificial Intelligence)    |
| `cs.CV`   | 计算机视觉 (Computer Vision)          |
| `cs.CL`   | 计算语言学 (Computation and Language) |
| `cs.LG`   | 机器学习 (Learning)                   |
| `stat.ML` | 机器学习 (Statistics)                 |

您可以访问 [arXiv Subject Classifications](https://arxiv.org/category_taxonomy) 页面查找所有可用的领域代码。

### 3. 运行脚本

配置完成后，在终端中进入脚本所在的文件夹，然后运行它：

```
python arxiv_daily_fetcher.py
```