# D4LCN 魔改 只用于单视图3D目标检测

##### 1. 创建环境

```
conda create -n wsd-D4LCN python=3.7
conda env list
conda activate wsd-D4LCN
conda install pytorch==1.11.0 torchvision torchaudio cudatoolkit=11.3
```

##### 2. 安装其他包

```
python -m pip install torchfile
python -m pip install numpydoc
python -m pip install numba 
python -m pip install visdom
python -m pip install opencv-python
python -m pip install easydict
python -m pip install Shapely
python -m pip install Cython
```

##### 3. 下载代码

```
git clone https://github.com/weishida666/D4LCN.git
```

##### 4. build the KITTI devkit eval for split1

```
sh data/kitti_split1/devkit/cpp/build.sh
```

##### 5. build the nms modules

```
cd lib/nms
make
```

##### 6. Testing

下载 [weights](https://drive.google.com/file/d/1EWrl6-brmrqKJakiTx5tGOE8DA5bdbbr)文件

放到根目录 /pretrain文件夹下

##### 7. 测试自己的数据

```
cd /root/autodl-tmp/weishida/code/D4LCN/D4LCN/data
mkdir test
cd test    分别放入图片对应的
mkdir calib    标定文件
mkdir depth  深度图
mkdir image   图像
输出会在 /root/autodl-tmp/weishida/code/D4LCN/D4LCN/output 文件下
python scripts/test.py
```

##### 8. 输出信息解释

```
000001.txt 文件内容
Car -1 -1 -1.487728 658.663757 192.247559 701.549500 225.237564 1.504116 1.642268 4.279702 3.493693 2.529841 36.805939 -1.393089 0.999019

cls,   类别 
alpha   角度              -1.487728
x1,     2Dbox  x1     658.663757
y1,     2Dbox  y1      192.247559
x2,     2Dbox  x2    701.549500 
y2,     2Dbox  y1      225.237564 
h3d,   3Dbox  h       1.504116 
w3d,   3Dbox  w     1.642268
l3d,    3Dbox  l       4.279702 
x3d,   3Dbox  x      3.493693 
y3d,   3Dbox  y      2.529841 
z3d,    3Dbox  z     36.805939
ry3d,   3Dbox旋转角   -1.393089
score    得分         0.999019
```

