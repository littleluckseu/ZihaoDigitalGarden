# 用 Graphviz 绘制关系图

一种自动化画图的方式。

---

## 背景

[Graphviz](http://www.graphviz.org/) 是个好东西，可用来绘制关系图。与 Visio 有一个本质上的差异： Graphviz 生成图是**自动布局**的，不需要手动调整元素的位置。当一个关系网络比较复杂时，用自动布局可实现**最小化连线交叉**。

![](https://image-backup-1253965369.cos.ap-guangzhou.myqcloud.com/Graphviz/Graphviz.png)

## 安装

发现一个很好用的在线编辑器：\[GraphvizOnline\]\([http://dreampuf.github.io/GraphvizOnline/\#digraph graph\_name { ](http://dreampuf.github.io/GraphvizOnline/#digraph%20graph_name%20{%20) %20%20A-&gt;B\[label%3D"关系"\]%20 }\) 支持即时渲染，导出 `.png` 与 `.svg` 等格式。

macOS 安装：`$ brew install graphviz`

## 作图流程

1. 新建 `xxx.dot`
2. 编辑 `.dot` 文档
3. 切换到所在目录，导出：`$ dot xxx.dot -T png -o xxx.png`

## 简易语法

```text
graph graph_name {
  A--B[label="连接关系"]
}
```

![](https://image-backup-1253965369.cos.ap-guangzhou.myqcloud.com/Graphviz/屏幕快照%202019-02-01%20下午2.02.44.png)

## FAQ

Q：其他平台的兼容情况？ A：官网有 Windows，macOS，Linux 的下载链接，推荐在线工具。

## 总结

自动布局是 Graphviz 的精髓。类比我之前用 Markdown 语法直接生成幻灯片，这些工具把内容标准化，让人能够**更加注重于内容，而非形式与布局**。

## 参考与致谢

* [Graphviz 简易教程](https://blog.zengrong.net/post/2294.html)
* [Drawing graphs with dot](http://www.graphviz.org/pdf/dotguide.pdf)
* [Windows 下 Graphviz 安装及入门教程](https://blog.csdn.net/lanchunhui/article/details/49472949)

