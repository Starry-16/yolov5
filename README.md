## 环境要求
python3.8及以上
还要安装requirements.txt文件中所有依赖包，包括1.7及以上版本的torch
~~~
pip install -r requirements.txt
~~~


## 测试
运行前先将图片或视频文件放在和detect.py同一目录下，然后运行下面语句：
~~~
python detect.py --source file.jpg --weights ./runs/train/exp_1000/weights/best.pt
~~~
其中file.jpg是图片文件名，best.pt是训练好的模型文件名，也可以使用last.pt，可以在runs/train/exp_1000/weights/目录下找到，exp_1000是训练过程中的日志文件夹，exp_1000中的1000是训练的epoch数，可以视情况修改。

## 训练自己的数据集
1. 下载数据集,并把它放在根目录下：[链接](https://pan.baidu.com/s/1BAgzqoNO6EAP61nksvQ_lA) ，提取码：asdf
2. 创建dataset.yaml文件，文件要满足以下格式（如下）：
~~~
// train and val data 
train: ./jsai_data/images/  # 2000 images
val: ./jsai_data/jpgs/  # 2000 images

// number of classes
nc: 8

// class names
names: ['Transverse_fracture', 'Longitudinal_fracture', 'Block_type_fracture', 'cracking', 'Pit_groove', 'Repair_mesh_cracks', 'Mend_the_cracks', 'Repai_of_potholes']
~~~
3. 创建标签文件
这里不需要自行创建，因为题目中已经给出

4. 选择模型
推荐选择YOLOv5s，小还快

4. 训练
~~~
python train.py --img 1088 --batch 16 --epochs 5 --data dataset.yaml --weights yolov5s.pt
~~~
