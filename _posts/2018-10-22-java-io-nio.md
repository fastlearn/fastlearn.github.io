---
layout: post
title: Java 基础知识回顾 - IO/NIO
category: [Java]
tags: [Java]
---

Java 的 I/O 大概可以分成以下几类：

- 磁盘操作：File
- 字节操作：InputStream 和 OutputStream
- 字符操作：Reader 和 Writer
- 对象操作：Serializable
- 网络操作：Socket
- 新的输入/输出：NIO

## 磁盘操作 FIle

File 对象表示一个文件或目录的信息，如名称，大小等，但它并不表示文件的内容。

以下是 File 对象的常见操作

### 文件操作

```java
// 表示一个文件在内存中还未持久化到磁盘
File file = new File("E:/a.txt");
if (!file.exists()) {
    // 新建文件，将文件从内存中持久化到磁盘
    file.createNewFile();
}
// 删除文件
file.delete();

```

### 目录操作

```java
// 表示一个目录
File dir = new File("E:/a/b/c");
if (!dir.exists()) {
    // 创建一级目录，父目录不存在创建失败,不会抛异常
    dir.mkdir();

    // 如果父目录不存在，自动创建父目录
    dir.mkdirs();
}
```

### 列出给定目录下所有文件

```java
public static void listFiles(String filePath) {
    listFiles(new File(filePath));
}

// 列出目录下的所有文件
public static void listFiles(File file) {
    if (file == null || !file.exists()) return;

    if (file.isFile()) {
        System.out.println(file.getName());
        return;
    }

    for (File file1 : file.listFiles()) {
        listFiles(file1);
    }
}
```

## 字节操作 InputStream / OutputStream

### 读取文件内容

```java
// 一个字节一个字节的读
public static void read1(String filePath) {
    try(InputStream is = new FileInputStream(filePath)) {
        int b;
        StringBuilder sb = new StringBuilder();
        while ((b = is.read()) != -1) {
            sb.append((char)b);
        }
        System.out.println(sb);
    } catch (IOException e) {
        e.printStackTrace();
    }
}

// 带缓冲区的读
public static void read2(String filePath) {
    try(InputStream is = new FileInputStream(filePath)) {
        StringBuilder sb = new StringBuilder();
        byte[] bytes = new byte[1024 * 10];
        int length;
        while ((length = is.read(bytes)) != -1) {
            sb.append(new String(bytes, 0, length));
        }
        System.out.println(sb);
    } catch (IOException e) {
        e.printStackTrace();
    }
}
```

### 写文件

```java
public static void write(String content, String src) {
    try(OutputStream fos = new FileOutputStream(src)) {
        fos.write(content.getBytes());
    } catch (IOException e) {
        e.printStackTrace();
    }
}
```

### 文件复制

```java
public static void copyFile(String src, String dist) {
    try (InputStream fis = new FileInputStream(src);
         OutputStream fos = new FileOutputStream(dist);){
        int length;
        byte[] bytes = new byte[1024 * 20];
        while ((length = fis.read(bytes)) != -1) {
            fos.write(bytes, 0, length);
        }
    } catch (IOException e) {
        e.printStackTrace();
    }
}
```

## 字符操作 Reader / Writer

### 编码与解码

编码就是把字符转换为字节，而解码是把字节重新组合成字符。

如果编码和解码过程使用不同的编码方式那么就出现了乱码。

- GBK 编码中，中文字符占 2 个字节，英文字符占 1 个字节；
- UTF-8 编码中，中文字符占 3 个字节，英文字符占 1 个字节；
- UTF-16be 编码中，中文字符和英文字符都占 2 个字节。

### 

不管是磁盘还是网络传输，最小的存储单元都是字节，而不是字符。但是在程序中操作的通常是字符形式的数据，因此需要提供对字符进行操作的方法。

- InputStreamReader 实现从字节流解码成字符流；
- OutputStreamWriter 实现字符流编码成为字节流。

### 逐行读取文件内容

```java
public static void read(String filePath) {

    try (FileReader fileReader = new FileReader(filePath);
         BufferedReader bufferedReader = new BufferedReader(fileReader);) {
        StringBuilder sb = new StringBuilder();
        String line;
        while ((line = bufferedReader.readLine()) != null) {
            sb.append(line);
        }
        System.out.println(sb);
    } catch (IOException e) {
        e.printStackTrace();
    }
}
```

