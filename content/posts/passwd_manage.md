---
title: "密码管理"
date: 2020-11-01T15:29:31+08:00
draft: true
---

{{< music auto="https://music.163.com/#/playlist?id=60198" >}}

## 背景&问题
现如今互联网飞速发展，各种服务层出不穷，随之而来的就是每个服务都需要注册账号，这必然给我在管理账号密码方面带来不小的烦恼
* 密码规则复杂， 生成麻烦
* 容易遗忘
* 需要手动输入
* 现有很多密码管理软件数据都不在自己手中，不放心

## 我的方案
基于以上问题， 我的解决方法如下：
* enpass（支持各平台）
* webdav, 通过webdav协议备份密码数据
* onedrive, 在win工作平台上， 将enpass文件放在onedrive中，使用onedrive同步

通过以上方式，可以做到数据的高可用，以及跨平台， 最后我只需要记住enpass的master密码就可以了

## 遗留
{{< admonition type=tip title="master密码忘记怎么办" open=false >}}
master密码忘记怎么办:upside_down_face:
{{< /admonition >}}
