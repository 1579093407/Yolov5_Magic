# 分享一些关于改进Yolov5的tricks以及实验结果
# Share some tricks of improving Yolov5  and experiment results

## 《Yolov5实验数据全部开源》

近期大家在我的博客看到了很多关于如何改进Yolov5的文章，其实我发的这些内容我都亲自进行了实验，因为数据集的关系每次实验都花费数个小时，但是我的改进并没有带来很大的提升，相反都带来的一些反向的提升；

我也尝试去复现别人论文里引入注意力机制的Yolov5结构，不知道为什么同样的参数却达不到人家的效果，我猜测可能是数据集的关系，并且还有一些其他的数据增强参数作者们是未公开的，我本人也是一名刚接触目标检测不久的在校生，所以很多东西还在探索中，我很清楚目前我们研究生所需要的东西，所以我准备把这段时间所作实验的结果全部开源，希望能给大家起到一些参考作用。当然不同的数据集效果肯定是不同的。

-----

有关代码怎么使用我就不过多介绍了，大家可以去看我的博文，或者官方的文档，我在这统一做一个汇总

1.[手把手带你调参Yolo v5 (v6.1)（一）](https://blog.csdn.net/weixin_43694096/article/details/124378167)🌟强烈推荐

2.[手把手带你调参Yolo v5 (v6.1)（二）](https://blog.csdn.net/weixin_43694096/article/details/124411509?spm=1001.2014.3001.5502)🚀

3.[如何快速使用自己的数据集训练Yolov5模型](https://blog.csdn.net/weixin_43694096/article/details/124457787)

4.[手把手带你Yolov5 (v6.1)添加注意力机制(一)（并附上30多种顶会Attention原理图）](https://blog.csdn.net/weixin_43694096/article/details/124443059?spm=1001.2014.3001.5502)🌟

5.[手把手带你Yolov5 (v6.1)添加注意力机制(二)（在C3模块中加入注意力机制）](https://blog.csdn.net/weixin_43694096/article/details/124695537)

6.[Yolov5如何更换激活函数？](https://blog.csdn.net/weixin_43694096/article/details/124413941?spm=1001.2014.3001.5502)

7.[Yolo v5 (v6.1)数据增强方式解析](https://blog.csdn.net/weixin_43694096/article/details/124741952?spm=1001.2014.3001.5502)

8.持续更新中

------

本人所用数据集是网络上购买的黑夜行人数据集（训练集9424，验证集2357，测试集3249），数据集只包含一个Person类别

这里简单展示一些数据集的内容


![image](https://user-images.githubusercontent.com/58406737/168735743-5348e476-1e31-4b78-84b7-ff7276e40dc4.png)






------

这里我也免费分享这个数据集，数据集已经划分成了Yolo的格式，大家下载后直接可以使用。

>百度网盘
>
>链接：https://pan.baidu.com/s/1L5noLQdLMbefw0O7bewojQ 
>提取码：4usm




------

实验结果

| Model             | epoch | freeze | multi_scale | mAP 0.5   | Parameters(M) | GFLOPs |
| ----------------- | ----- | ------ | ----------- | --------- | ------------- | ------ |
| Yolov5s           | 300   | 0      | false       | **0.953** | Nan           | Nan    |
| Yolov5s           | 120   | 8      | false       | 0.936     | Nan           | Nan    |
| Yolov5s_SE        | 120   | 7      | false       | 0.874     | Nan           | Nan    |
| Yolov5s_ECA       | 200   | 7      | false       | 0.937     | Nan           | Nan    |
| Yolov5s_CBAM      | 200   | 7      | **true**    | 0.882     | Nan           | Nan    |
| Yolov5s_BiFPN     | 200   | 7      | false       | 0.935     | Nan           | Nan    |
| Yolov5s_BiFPN_ECA | 200   | 0      | false       | 0.951     | Nan           | Nan    |

------


还有一些其他tircks的实验结果我正在整理中，后续我会更新在Github的

如果可以,我也希望大家可以把自己用到的一些涨点的技巧分享出来

