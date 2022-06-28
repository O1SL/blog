---
title: "数值统计5"
date: 2022-06-27T16:48:09+08:00
draft: false
author: ["WuJunlin"]
categories: 
- 娱乐
tags: 
- Hugo
- Blog
description: ""
weight: # 输入1可以顶置文章，用来给文章展示排序，不填就默认按时间排序
slug: ""
comments: false
showToc: false # 显示目录
TocOpen: true # 自动展开目录
hidemeta: false # 是否隐藏文章的元信息，如发布日期、作者等
disableShare: true # 底部不显示分享栏
cover:
    image: ""
    caption: ""
    alt: ""
    relative: false
---
# 统计描述_数值方法

## 位置的度量

样本：xi、n 
总体：xi、N 

- 平均数mean 
- 加权平均数weighted mean 
- 中位数（排序为升序）median 
- 几何平均数geometric mean ：n个数值乘积的n次方根 x−g

 常用于分析财务数据的增长率，其他通常应用包括物种总体、农作物产量等，例如每年的投资回报就是用几何平均数描述，算术平均数不能描述，因为投资回报率是每年相乘的 

注意回报率和增长因子的关系，描述的是回报率-28%，实际计算需要使用增长因子0.72 

5. 众数mode 
6. 百分位数percentile 

LP提供了数据如何散布在从最小值到最大值的区间上的信息。对于包含n个观测值的数据集，第p百分位数将数据分割为两个部分：大约有p%的观测值比第p百分位数小，大约有1-p%的观测值比第p百分位数大 

𝑳𝐩 =𝒑𝟏𝟎𝟎∗(𝒏+𝟏)

 

Lp是个位置，的到的结果是5位、6位、10.4位这样的，利用这个位置去升序排列的数据中去找到对应的观测值，10.4位的值等于第10位到第11位中间线性0.4的那个数值 

7. 四分位数quartiles 

将数据划分为4部分 

Q1=第一四分位数，或第25%百分位数 

Q2=第二四分位数，或第50%百分位数--中位数 

Q3=第三四分位数，或第75%百分位数 

数据中含有极端值的时候，使用中位数作为中心位置的度量比平均数更合适