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
# Light network
## Mobile Net V1
