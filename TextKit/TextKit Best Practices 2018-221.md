链接：[2018 session 221](https://developer.apple.com/videos/play/wwdc2018/221/)

## 层级

![img](2018-221/001.png)

## 如何选择

![img](2018-221/002.png)

![img](2018-221/0021.png)

![img](2018-221/003.png)

## 复杂文本定制方案

类似于 MVC 的架构模式：

![img](2018-221/004.png)

###### 1. Storage

![img](2018-221/0041.png)

1. NSTextStorage：存储 字符串数据和属性信息
 
 	![img](2018-221/00411.png)
	
2. NSContainer：定义文本布局的几何区域

	![img](2018-221/00412.png)
	
详情：

 * wwdc12 `Introduction to Attributed Strings for iOS`
 * wwdc12 `Advanced Attributed Strings for iOS`

 
###### 2. Display
 
 ![img](2018-221/005.png)
 
 更多：
 
 * Text Programming Guide for iOS
 * Text System User Interface Layer Programming Guide
 
###### 3. Layout
 
 ![img](2018-221/006.png)
 
NSLayoutManager: 协调 Storage 和 Display，控制布局流程，**负责字形生成和字形布局**。

![img](2018-221/007.png)


更多：wwdc13:`Advanced Layouts and Effects With Text Kit`
 
 
## 配置方案

1. 标准方案：

	![img](2018-221/0081.png)
	
2. 相同布局，不同展示方案：

	![img](2018-221/0082.png)

3. 不同布局方案：

	![img](2018-221/0083.png)
	
	
更多：wwdc2010 `Advanced Cocoa Text Tips and Tricks`

## 定制化方案

代理--通知--子类化。定制程度依次增强。

![img](2018-221/00110.png)

###### 1. 顶部 UILable 示例

![img](2018-221/009.png)

实现方案：

![img](2018-221/0091.png)
![img](2018-221/0092.png)

###### 2. 多行可选 UITextView 示例：

![img](2018-221/0010.png)

![img](2018-221/0011.png)


## Markdown 解析文本框

![img](2018-221/00110.png)

1. 简单字数统计：使用 通知 方案

	![img](2018-221/00121.png)
	![img](2018-221/00122.png)
	
2. markdown 加粗：代理 方案

	![img](2018-221/00131.png)
	![img](2018-221/00132.png)
	
3. markdown 代码引用： 子类化

	![img](2018-221/00141.png)
	![img](2018-221/00142.png)
	![img](2018-221/00143.png)
	![img](2018-221/00144.png)
	![img](2018-221/00145.png)

## Markdown 左右视图展现方案：

![img](2018-221/00154.png)

1. 实现方案：

	![img](2018-221/00151.png)

2. UI 组织：

	![img](2018-221/00152.png)

3. 代理方案清除 markdown 字符：

	![img](2018-221/00153.png)
	
	

更多：

* Text Programming Guide for iOS
* Cocoa Text Architecture Guide
* Introduction to Text Layout Programming Guide

	
## 正确设置

###### 1. 关于默认属性问题

![img](2018-221/00164.png)

一段字符串默认为 Helvetica 12，则错误示例：

![img](2018-221/00161.png)

1. 解决方案一：避免混合使用纯文本和属性文本：
	
	![img](2018-221/00162.png)
	
2. 以纯文本创建特定默认属性文本：

	![img](2018-221/00163.png)
	

###### 2. 段落问题

1. 应用段落属性忽略最后一个文字（但错误结果如右下角，原因同上，默认值问题）：


	![img](2018-221/00171.png)



###### 3. 非连续布局

* 布局策略时机：

	![img](2018-221/00181.png)
	
* 连续布局问题：

	![img](2018-221/00182.png)

* 非连续布局优势：

	![img](2018-221/00183.png)
	
	
1. 在 `UITextView` 中设置非连续布局（默认值）：
	
	``(layout manager)allowsNonContiguousLayout``
	
2. 在非连续布局下，避免一次性执行全文本布局请求

	![img](2018-221/00184.png)
	
更多：wwdc2017 Efficient Interactions with Frameworks



## 安全

深层防护（综合防护）

![img](2018-221/00191.png)


1. 文本输入限制（如长度）

