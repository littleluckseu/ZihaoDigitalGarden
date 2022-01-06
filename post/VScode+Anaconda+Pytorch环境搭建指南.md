自己花了大半天的时间终于把这个环境搭建好了，写个笔记提醒其他想要搭建的童鞋，避免踩坑。

我发现主要的踩坑地方可能发生的千奇百怪，一个坑连着另外一个坑，当你乱七八糟地安装了一堆包之后，最好的办法就是**卸载重来**。 这个方法是我目前发现的最有效的方式，不然你就会莫名其妙地报了一个错，然后在网上死活也搜不到解决办法。 

## Anaconda下载 
1. 官网下载
[Anaconda | Individual Edition](https://www.anaconda.com/products/individual) 

没什么好说的，直接官网下载即可。 
 
2. 安装步骤 

安装步骤详见这篇链接，我直接转载了，大家安装详细的步骤设置即可。 

[手把手教你如何在 Windows 安装 Anaconda - SegmentFault 思否](https://segmentfault.com/a/1190000037752539)

这里要注意环境变量的配置，我个人建议是不勾选自动配置，然后自己手动去添加，具体的方式见上面链接。 

## Pytorch环境配置 

首先在Anaconda里面创建一个虚拟环境来安装Pytorch。那么什么是虚拟环境呢？

我们来假设这么一个场景，假如说你的一个程序要用到Python2+tensorflow，另外一个程序要用到Python3+Pytorch，那么你肯定不能直接把它们装在你的电脑里，因为这样做会导致你整个的环境混乱，程序不知道该用那个版本的Python。

Anaconda的好处就在于你可以自己创建一个新的环境，当你需要使用时直接切换环境运行程序就不需要造成上述问题了。 

我们就不用命令行来了，打开Anaconda Navigator（这是图形化的操作页面），在Environments的界面选择新建一个环境。

![](https://image-upload-1307521651.cos.ap-nanjing.myqcloud.com/picture_upload/20211204114022.png)

这里比如说我要创建Pytorch环境，那么我直接输入Pytorch（名字可以随便取），Python版本会自动推荐，然后直接创建即可。 

创建完成之后，我们需要到Pytorch的官网寻找安装的命令。 

[PyTorch](https://pytorch.org/) 

一般来说，当你打开这个页面，它会自动给你推荐你当前适合的版本，所以直接复制那段命令行代码即可。 

![](https://image-upload-1307521651.cos.ap-nanjing.myqcloud.com/picture_upload/20211204114329.png)

```
conda install pytorch torchvision torchaudio cudatoolkit=10.2 -c pytorch （不要复制这里，自己去官网看，如果没有独显建议也选择有CUDA的版本，反正是兼容的，当然你也可以仅仅选择CPU的版本）
```

之后打开之前Pytorch目录下的终端，添加清华镜像，不然很有可能出现网络断开崩掉的情况。 

按照下图打开终端，当然你也可以打开Anaconda的命令行终端Anaconda Prompt，输入 activate Pytorch（你的环境名字），二者的功能是一样的。 
![](https://image-upload-1307521651.cos.ap-nanjing.myqcloud.com/picture_upload/20211204114807.png)

复制下面代码到终端里，添加清华镜像，不然你下载Pytorch可能会失败。

```
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/

conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/

conda config --set show_channel_urls yes

conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
```


复制之前在Pytorch官网的安装代码，回车,弹出提示，选择Y安装即可。 

如果成功安装，命令行窗口会显示done，显示安装成功。 


## Vscode

默认你已经配置好Vscode + Python环境，这个很简单，自己去找教程即可。 

随便打开一个py文件或者Jupyter的文件，可以看到左下角或者右上角会让你选择当前的环境，选择你需要的环境即可。 

之后运行代码就可以看到成功咯。 

如果缺少相关的包，可以看看错误提示，然后在之前的环境命令行的下输入：

```
conda install 缺失的包名
```
![](https://image-upload-1307521651.cos.ap-nanjing.myqcloud.com/picture_upload/20211204115814.png)

安装完重启Vscode就会发现错误已经没了。 

## 问题解决

我在安装的过程中也出现了各种各样的问题，比如说ipykernel无法安装，导致使用不了Jupyter Notebook（这里需要注意的是目前这个功能已经集成在Vscode Python的插件里了，不需要单独安装）。

如果你在当前环境了安装了各种乱七八糟的包，然后还是没有解决问题，最好的方式就是删除当前环境下所有安装的包。 

```
conda clean --all
```

然后重新再来！ 真的亲测有效，很多时候就是之前的包缓存没删干净，或者安装的先后顺序不对导致失败的。这样的错误你在网上也搜不到，不如重来~ 

## 资源安利 

推荐一波我觉得很好的Pytorch的基础教程： 

下面第一个强推，国外的视频是真的做的好。 
 [Deeplizard《Pytorch神经网络高效入门教程》中文字幕版_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1UE411N7pD?p=2)
 
[PyTorch Prerequisites - Syllabus for Neural Network Programming Course - deeplizard](https://deeplizard.com/learn/video/v5cngxo4mIg)

实践必看，基本上把AI相关的知识串起来了，适合小白入门。 

[《PyTorch深度学习实践》完结合集_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1Y7411d7Ys?p=1)
 
必读书目网盘链接，偷偷告诉你里面还有很好的AI综述课程，帮你建立宏观的图景。 

 ## 参考
- [Anaconda+pyTorch+VScode安装配置说明_summerbell-CSDN博客](https://blog.csdn.net/summerbell/article/details/117593456) 
- [pytorch+anaconda+vscode深度学习环境配置（GPU）hengyuling2002的博客-CSDN博客](https://blog.csdn.net/chengyuling2002/article/details/119513278)