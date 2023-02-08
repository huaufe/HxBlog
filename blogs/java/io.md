---
title: io
date: 2023-2-8
tags:
 - io
categories:
 -  java
---


::: tip 介绍
1. IO文件流；<br>
:::

## lambda表达式

**list分组**

``` java
    // 图片文件下载
    public static boolean upload(String imageUrl) {
        boolean flg = true;
        try {//new一个URL对象
            URL url = new URL(imageUrl);
            HttpURLConnection conn= (HttpURLConnection) url.openConnection();
            conn.setRequestMethod("GET");
            conn.setConnectTimeout(60);//超时提示1秒=1
            //打开链接
            InputStream inStream = conn.getInputStream();
            byte[] bs = new byte[1024];
            String filename = "D:\\DATA/" + "测试" + ".jpg";
            File file = new File(filename);
            FileOutputStream os = new FileOutputStream(file, true);
            int len;
            while ((len = inStream.read(bs)) != -1) {
                os.write(bs, 0, len);
            }
            os.close();
            inStream.close();
        } catch (Exception e) {
            e.printStackTrace();
            flg = false;
        }
        return flg;
    }
    // 根据路径下载
    public static void main(String[] args) {
        boolean upload = upload("https://gimg2.baidu.com/image_search/src=http%3A%2F%2Flmg.jj20.com%2Fup%2Fallimg%2F1114%2F033021091503%2F210330091503-6-1200.jpg&refer=http%3A%2F%2Flmg.jj20.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1675481452&t=ef3361e4337fed50bb97bbffed8e6a76");
        System.out.println(upload);
    }
```

