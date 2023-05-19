##  ubuntu 下yolov5 训练 pascal voc 数据集

问题1：出现字体下来不了的情况。

下载到本地，复制到目录下

参考链接：

https://blog.csdn.net/qq_36756866/article/details/109111065



```
# rar解压必须要加上 x
unrar x a.rar
```



# 标准文件层级格式

- VOCData
  - labels  # yolo格式标注文件  # 由voc_label.py生成
  - test.txt  # 训练集的路径文件  # 由voc_label.py生成
  - train.txt  # 测试集的路径文件  # 由voc_label.py生成
  - val.txt  # 验证集的路径文件  # 由voc_label.py生成
  - ~~dataSet_path  # 三个数据集的路径文件~~
    - ~~test.txt~~
    - ~~train.txt~~
    - ~~val.txt~~
  - Annotations  # 注释文件
  - images  # 图片文件 【重点来了】存放图片的文件夹一定要是这个名字，否则就会报错 labels not found
  - ImageSets  # 由voc_split_trainVal.py生成
    - Main  # 图片名字文件，无后缀.jpg
      - test.txt
      - train.txt
      - trainval.txt
      - val.txt





参考链接：https://blog.csdn.net/weixin_48780159/article/details/119461483 【重点链接】

https://blog.csdn.net/qq_45945548/article/details/121701492

https://blog.csdn.net/qq_51331745/article/details/121791008

https://blog.csdn.net/weixin_50113231/article/details/123566563







 C. 不使用预训练权重，从头开始训练：

```
python train.py --img 640 --batch 16 --epochs 300 --data ../orange-detection1/data.yaml --cfg models/yolov5s.yaml --weights ''
```

https://blog.csdn.net/weixin_49929808/article/details/120357725



## 在Ubuntu上使用yolov5-6.0训练自定义数据集步骤

一. 标注图片

​	 图片文件夹 images

​	 标注文件夹 Annotations



二. 数据集曾广

​	 运行 augment_tools 文件夹下的 color.py 和 flip.py 文件，得到曾广后的数据集



三. 生成ImageSets文件夹

​	 运行 voc_split_trainVal.py 文件，得到 ImageSets文件夹



四. 生成labels文件夹 和 train.txt、val.txt 和 test.txt

​	  运行 voc_label.py 文件，得到 labels文件夹 和 train.txt、val.txt 和 test.txt



五. 修改配置文件，进行训练

​		修改models文件下的配置文件和data文件夹下面的配置文件





```
scp C:/Users/Lenovo/Desktop/yolov5m.pt simple@192.168.8.44:/home/simple/Desktop/yolov5/weights
scp C:/Users/Lenovo/Desktop/gesture_datasets.rar simple@192.168.8.44:/home/simple/Desktop
scp C:/Users/Lenovo/Desktop/GestureDatasets.rar simple@192.168.8.44:/home/simple/Desktop

scp F:/my_Code/Datasets_made_tool/数据集处理/voc_split_trainVal.py simple@192.168.8.44:/home/simple/Desktop

scp C:/Users/Lenovo/Downloads/SunloginClient_11.0.1.44968_amd64.deb simple@192.168.8.44:/home/simple/Desktop
```

/home/simple/Desktop/gesture_datasets/v1

python train.py --epochs 10 --cfg models/yolov5s_gesture_v1.yaml --data data/VOC_gesture_v1.yaml --weights weights/yolov5s.pt

python train.py --epochs 10 --cfg models/yolov5m_gesture_v1.yaml --data data/VOC_gesture_2224_v1.yaml --weights weights/yolov5m.pt



python detect.py --weights /home/simple/Desktop/yolov5/runs/train/exp/weights/best.pt --source 0
