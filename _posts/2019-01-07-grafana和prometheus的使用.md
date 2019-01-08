---
layout: post
title: 'grafana'
date: 2018-11-29
categories: grafana
cover: https://image.mmschool.club/github/wolf.jpg
tags: 监控
---

我在上家公司就接触过Grafana, 当时是对web访问接口的监控，公司好像也是说有这个东西就行了，我也没有太在意这个东西。
直到现在这家公司，领导让我部署一个grafana的服务，我这才仔细的看了看个东东。

## 现状
项目的代码中的对于metric值的已经写好，单独有个包可以调用，每个项目的metric值是用户自定义的。用于统计错误数量，
成功处理的数据量。数据接收后统一发送到一个Kafka消息队列。现在需要消费Kafka中的数据，将数据发送到prometheus

## 初步探索
我需要建立个小服务，将metric值取过来，本地的缓存最新的值

## 问题
prometheus 会定时的去我部署的服务拉取数据，但是拉取是有间隔的。我不能忽略任何值。

## 解决
去github上看，有个pushgateway,这是一个可以缓存很多metrics值的一个中间服务。prometheus定时从这个节点将数据取回
算是解决了问题

## 坑
pushgateway有个坑，如果你传过来的值是重复的，就会报错，然后整个在prometheus可以看到整个pushgateway服务不可用，
这个很坑了，有的metric值就是很长时间不会变化的。

## 最后
还是用最老的方法，将数据写入我自己建立的服务，将时间设为每秒一次。


