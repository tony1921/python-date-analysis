## Netflix 电影演员评分数据整理（数据分析项目）
本项目通过对 Netflix 影视作品及演员出演信息进行清洗、整理、合并与统计，最终得到 各个流派（Genre）中演员的平均 IMDB 评分，为后续挖掘高分演员、分析流派表现等提供结构化的数据基础。

该项目重点练习数据清洗、字段解析、字符串处理、分类整理与分组统计等。

#### 1. 项目目标（Project Objective）

从原始 Netflix 影视数据中提取出：电影  剧集、演员、IMDB 评分、流派（Genre）等核心字段

处理多演员、多流派、多标签等复杂字段

清洗不规范数据（缺失、重复、格式混乱等）

合并两张表，得到“演员-作品-评分-流派”完整结构

计算每位演员在不同流派的平均评分

最后输出一个干净、可直接用于模型或分析的数据集


#### 2. 数据说明（Datasets）

原始数据来源于 Netflix 截止 2022 年 7 月的全量影视内容数据。

包含两个主要数据表：

titles.csv	Netflix 所有影片与剧集，包含名称、类型、时长、IMDB/烂番茄评分、流派（Genre）等

credits.csv	演员 & 导演出演信息，包括姓名、角色、作品 ID、演职员类型等

清洗后输出的数据文件：

cleaned_actor_scores.csv	已清理结构化的“演员-流派-平均评分”结果数据

actor_score_by_genre.csv	含分组统计结果的最终表格

#### 3. 使用的技术（Tech Stack）

Python 3

pandas：数据清洗与表格操作

numpy：数值处理

Jupyter Notebook：分析主环境

#### 4. 数据清洗步骤（Data Cleaning Steps）

Notebook（完成版.ipynb）中主要执行了如下清洗步骤：

✅ (1) 读取两张原始数据表

加载 titles.csv

加载 credits.csv

✅ (2) 处理 titles 表

保留“Movie / TV Show”与评分相关字段

拆分多 Genre（如 "Comedy, Drama" → 列表）

清洗 IMDB 与 Rotten Tomatoes 评分

过滤空值、异常值、无评分的数据

✅ (3) 清洗 credits 表

仅保留 演员（Actor） 数据

去除导演、无名字段

清理重复出演记录

统一演员名字与 ID

✅ (4) 合并两张表

✅ (5) 多演员、多流派拆解

一部作品可能有多个演员

一个作品包含多个流派
本项目使用 explode 将列表展开成多行，使每对“演员-流派”都成为结构化记录。

✅ (6) 分组分析

根据 Notebook： groupby(["Actor", "Genre"])["IMDB"].mean()
得到每位演员在每个流派的平均评分。

#### 最终生成干净可用的数据表


#### 5. 分析结果与洞察（Results & Insights）

Notebook 最终得到：

⭐ 1. 每位演员在不同流派中的评分分布

例如某演员在 Comedy、Action、Drama 中的平均 IMDB 分别是多少。

⭐ 2. 可筛选高评分演员


#### 7. 如何运行项目（How to Run）
1. 安装依赖
pip install pandas numpy

或根据 requirements.txt：

pip install -r requirements.txt

2. 打开 Notebook
jupyter notebook

打开：

04 项目实战 _ 整理Netflix电影演员评分数据（完成版）.ipynb


即可完整复现流程。
