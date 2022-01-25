# deep_learning_paper_read_lists

# Learning invariace to spatial transformation
## [2015 NIPS saptial transoformer networks](https://proceedings.neurips.cc/paper/2015/file/33ceb07bf4eeb3da587e268d663aba1a-Paper.pdf)
文章通过替换网络模块，采用无监督的方式使得网络具备空间表达能力，学习对平移、尺度、旋转和其他几何形变保持不变的能力。max-pooling 存在局部的空间不变性，却难以适应大尺度的空间变化。
* （其实空间的不变性和感受野是强相关的）
作者提出了spatial transformers 用于替换原本的卷积层。实现的spatial transformers 包括三个部分，
* 第一部分是定位网络：从输入的特征中学习空间变换的参数（注意所有的通道对应同一套参数）
* 第二部分grid generator：预测的参数用于制作sampling grid，采样网络定义了输入采样对应输出的位置
* 第三部分：将sampling grid和输入特征联合输入，得到输出

## [2017 CVPR Deformable Convolutional Networks](https://openaccess.thecvf.com/content_ICCV_2017/papers/Dai_Deformable_Convolutional_Networks_ICCV_2017_paper.pdf)
文章提出可形变deformable convolution和deformable RoI pooling，提升卷积层的空间表达能力。作者在输入特征的每个grid位置学习了offsets，实现具有offsets的卷积和池化。
* STN对全部通道学习了一个global参数，DCN学习的local offsets.

# Light model
## Network architecture
### [MobileNets: Efficient Convolutional Neural Networks for Mobile Vision Applications](https://arxiv.org/pdf/1704.04861.pdf%EF%BC%89)

链接：https://arxiv.org/pdf/1704.04861.pdf%EF%BC%89

一个三维的卷积，可以展开为一个二维的卷积和一个一维的卷积，也就是作者讲的depthwise convolutions and pointwise convolutions。
其中depthwise convolutions 相同与普通的卷积，与网络中的卷积不同的是，它仅仅对每单个通道进行处理；
pointwise convolutions是一个1*1的卷积，但对所有的输入通道进行卷积

作者思想类似于传统卷积操作中常用的分离卷积用于卷积加速计算，解释详见个人博客：https://blog.csdn.net/zseqsc_asd/article/details/109559972?spm=1001.2014.3001.5501

## Re-parameterization
### [RepVGG: Making VGG-style ConvNets Great Again](https://openaccess.thecvf.com/content/CVPR2021/papers/Ding_RepVGG_Making_VGG-Style_ConvNets_Great_Again_CVPR_2021_paper.pdf)
链接：https://openaccess.thecvf.com/content/CVPR2021/papers/Ding_RepVGG_Making_VGG-Style_ConvNets_Great_Again_CVPR_2021_paper.pdf
重参数化是一种将多分枝的拓扑结构模块(例如resnet)在推理阶段转换为plain模块，提升推理性能。具体实现是，3 * 3， 1 * 1， skip connection 可以整合为一个3 * 3的 卷积层，多个BN通路也可以整合为一个BN通路，最终将多通路转换为但通路模块，极大降低推理时的算法性能。
