# 基于新闻数据的多路召回实践

***持续更新ing***

***敬请期待***

## 目录结构

```
NewsRecall:.
│  00sample.ipynb
│  01itemcf_i2i_sim.ipynb
│  02usercf_u2u_sim.ipynb
│  03item_embedding_sim.ipynb
│  04YouTubeDNN.ipynb
│  05item_recall.ipynb
│  06embedding_item_recall.ipynb
│  07user_recall.ipynb
│  08user_embedding_sim.ipynb
│  09embedding_user_recall.ipynb
│  main.py
│  README.md
│
└─data
    ├─generate
    │      embedding_sim_item_recall.pkl
    │      emb_i2i_sim.pkl
    │      itemcf_i2i_sim.pkl
    │      itemcf_recall_dict.pkl
    │      item_youtube_emb.pkl
    │      usercf_u2u2i_recall.pkl
    │      usercf_u2u_sim.pkl
    │      user_youtube_emb.pkl
    │      YGQ.csv
    │      youtubednn_usercf_recall.pkl
    │      youtube_u2i_dict.pkl
    │      youtube_u2u_sim.pkl
    │
    └─raw
            articles.csv
            articles_emb.csv
            testA_click_log.csv
            train_click_log.csv
```

## 召回方案

1. YouTubeDNN
2. item_recall
   * 根据{user1: [(item1, time1), (item2, time2)..]...}计算item的相似矩阵
   * 根据相似矩阵召回（关联规则）
3. embedding_item_recall
   * 根据item的向量相似度计算并召回

2. user_recall
   * 根据{item1: [(user1, time1), (user2, time2)...]...}计算user的相似矩阵
   * 根据相似矩阵召回（关联规则）
3. embedding_item_recall
   * 根据YouTubeDNN步骤中生成的用户部分历史序列的embedding
   * 计算相似度并召回

## 数据来源

| 名称                | 大小                                           | Link                                                         |
| ------------------- | ---------------------------------------------- | ------------------------------------------------------------ |
| articles.csv        | 9.89MB                                         | http://tianchi-competition.oss-cn-hangzhou.aliyuncs.com/531842/articles.csv |
| articles_emb.csv    | 973.15MB(MD5:1f8a7fc79e0ad13311e27e3408d0287b) | http://tianchi-competition.oss-cn-hangzhou.aliyuncs.com/531842/articles_emb.csv |
| testA_click_log.csv | 20.47MB                                        | http://tianchi-competition.oss-cn-hangzhou.aliyuncs.com/531842/testA_click_log.csv |
| train_click_log.csv | 43.5MB                                         | http://tianchi-competition.oss-cn-hangzhou.aliyuncs.com/531842/train_click_log.csv |
