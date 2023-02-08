---
title: geoserver发布乱码问题
date: 2023-02-08
tags:
 - geoserver
categories:
 -  linux
---


::: tip 介绍
1. geoserver显示乱码；<br>
:::

## Geoserver字符乱码问题

- 复制windows路径下字体到linux服务器的/usr/share/fonts/my_fonts路径下

```
C:\Windows\Fonts
```

- linux机器安装字体

```shell
# 安装字体索引指令
yum install mkfontscale
# 生成字体索引
cd  /usr/share/fonts/my_fonts
mkfontscale
```

- 映射geoserver的字体路径

```
version: '3'
services:
  geoserver:
    restart: always
    image: oscarfonts/geoserver
    container_name: geoserver
    volumes:
      - ./data_dir:/var/local/geoserver
      - ./plugin:/var/local/geoserver-exts/
      - /usr/share/fonts/:/usr/share/fonts/ # 此处将宿主机字体映射到容器中，解决发布图层中文乱码问题
    ports:
      - "8060:8080"
```

- 进入容器内部

```
docker exec -it geoserver /bin/bash
```

- 使字体生效

```
# 生成字体索引
cd /usr/share/fonts/my_fonts
mkfontscale
```



### 其他注意

- 对于中文shp文件，DBF文件类型指定为GBK，如果设置style样式，字体与数据存储格式保持一致。
- style中属性名与发布的服务属性名大小写保持一致

