train mtcnn: a modified version by Zuo Qing from https://github.com/Seanlinx/mtcnn

训练环境windows 7/10, 其他环境未测试

# 基本说明

**(1)请使用[ZQCNN_MTCNN](https://github.com/zuoqing1988/ZQCNN)来进行forward**

**(2)Pnet改为Pnet20需要在你的MTCNN中更改cell_size=20, stride=4**

	1920*1080图像找20脸，第一层Pnet20输入尺寸1920x1080，计算量347.9M，原版Pnet输入1152x648，计算量1278.0M

**(3)Rnet保持size=24不变，网络结构变为dw+sep，计算量约为原版1/3**

**(4)Onet暂时没有训练，等陆续更新**

# 训练建议

**(1)下载[WIDER_train](https://pan.baidu.com/s/1PSR11Xs8lWmtVazCGoYR7Q)解压到data文件夹**

	解压之后目录为data/WIDER_train/images

**(2)双击gen_anno_and_train_list.bat**

	生成prepare_data/wider_annotations/anno.txt和data/mtcnn/imglists/train.txt

## 训练Pnet20 

**(3)双击P20_gen_data.bat**

	生成训练Pnet20所需样本
	
**(4)双击P20_gen_imglist.bat**

	生成训练Pnet20的list文件

**(5)双击P20_train.bat**

	训练Pnet20
	
**(6)双击P20_gen_hard_example.bat**

	利用训练得到的Pnet20模型，生成用于进一步训练Pnet20的hard样本，请用文本方式打开，酌情填写参数
		
**(7)双击P20_gen_imglist_with_hard.bat**

	生成用于进一步训练Pnet20的list文件
	
**(8)双击P20_train_with_hard.bat**
	
	进一步训练Pnet20
	
## 训练Rnet

**(9)双击R_gen_data.bat**

	生成训练Rnet所需样本
	
**(10)双击R_gen_hard_example.bat**
	
	利用训练得到的Pnet20模型，生成用于训练Rnet的hard样本，请用文本方式打开，酌情填写参数
	
**(11)双击R_gen_imglist_with_hard.bat**

	生成用于训练Rnet的list文件
	
**(12)双击R_train_with_hard.bat**

	训练Rnet
	
## 训练Onet

**(13)双击O_gen_data.bat**

	生成训练Onet所需样本
	
**(14)双击O_gen_hard_example.bat**
	
	利用训练得到的Pnet20、Rnet模型，生成用于训练Onet的hard样本，请用文本方式打开，酌情填写参数
	
**(15)双击O_gen_imglist_with_hard.bat**

	生成用于训练Onet的list文件
	
## 不带landmark
**(16)双击O_train_with_hard.bat**

	训练Onet
	
## 带landmark

需要下载[celeba](https://pan.baidu.com/s/1rUBW8NasLZGtfQ33uA6Kdg)，并解压到data/img_align_celeba

图片位置在data/img_align_celeba/xx.jpg

**(17)双击O_gen_landmark.bat**

	生成训练Onet所需landmark样本

**(18)双击O_gen_imglist_with_hard_landmark.bat**

	生成用于训练Onet的list文件

## 单独训练landmark

**(19)双击L_train.bat**

	训练Lnet

 
