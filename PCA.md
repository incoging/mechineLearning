## PCA

### 为什么PCA不被推荐用来避免过拟合？

PCA只关注了输入之间的correlation。(supervised) learning寻求的是输入和输出之间的联系。
想象一个极端情况：输入的snr很低且噪声强相关，但是被学习的系统有超强能力完全忽略噪声。如果使用PCA，估计很可能只保留了噪声。
如果想要强调输入输出之correlation，不妨试试partial least square regression.

PCA是**无监督**的，没有考虑输入和输出之间的联系。所以它虽然能解决过拟合问题，但又会带来欠拟合问题。拿人脸识别来说，eigenface虽然能训练出识别能力尚可的分类器，但因为分类信息并不一定存在于前几个主成分上，所以用前几个主成分来做分类的话，会丢失后面变化细微的主成分上存在的大量分类信息。正因为如此，之后又出现了fisherface等有监督降维工作，识别能力也因此提高了很多。

深度学习也是这样，pre-training阶段很多训练都是无监督的（比如用自编码进行特征提取，预训练网络），其实和PCA异曲同工，但之后一定要有进一步的fine-tuning，把无监督提取出来的特征transfer到我们的目标任务上，这样得到的特征才真正work。 

 

 

 

 

 

 

 

 

 