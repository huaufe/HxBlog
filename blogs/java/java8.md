---
title: java8
date: 2023-2-8
tags:
 - io
categories:
 -  java
---

::: tip 介绍
1. java8基础用法；<br>
:::

## lambda表达式

**list分组**

``` java
Map<String,List<Qsdwdm>> map = myList.stream().collect(Collectors.groupingBy(o -> o.getQsdwdm());
```

**list转map**

``` java
Map<String, String> map = XjxzqList.stream().collect(Collectors.toMap(s -> s.getXzqdm(), t -> t.getXzqmc(), (o1, o2) -> o2));
```

**指定字段转为list**

``` java
List<String> sqids = getRecords().stream().map(ZjdSqJcxx::getSqid).collect(Collectors.toList());
```
