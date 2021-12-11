# NoiseFilter  
本篇文章将会涵盖下述几个方面：  
1. 讲解3种基本的噪声，包括高斯噪声、均匀分布噪声和椒盐噪声，的形成原因以及它们的概率密度函数。  
2. 掌握使用matlab模拟生成噪声的操作，探明不同参数的噪声如何干扰图像。  
3. 对10种典型的滤波器，包括算数均值滤波、几何均值滤波、谐波均值滤波、逆谐波均值滤波、中值滤波器、最大值滤波器、最小值滤波器、
中点滤波器、修正后的alpha均值滤波器、自适应中值滤波器，滤除噪声的能力进行探究和比较。  
---
# 目录
* [3种基本噪声](#3种基本噪声)
  * 高斯噪声
  * 均匀分布噪声
  * 椒盐噪声
* [10种典型滤波器](#10种典型滤波器)
  * 算数均值滤波
  * 几何均值滤波
  * 谐波均值滤波
  * 逆谐波均值滤波
  * 中值滤波器
  * 最大值滤波器
  * 最小值滤波器
  * 中点滤波器
  * 修正后的alpha均值滤波器
  * 自适应中值滤波器
* [总结](#总结)
* [参考文献](#参考文献)
---
# 3种基本噪声  
## 高斯噪声
### 定义
高斯噪声是指它的概率密度函数服从高斯分布（即正态分布）的一类噪声。常见的高斯噪声包括起伏噪声、宇宙噪声、热噪声和散粒噪声等等。  
在数字图像中的高斯噪声的主要来源出现在采集期间，由于不良照明和/或高温引起的传感器噪声。用于噪声去除的常规空间滤波技术包括：平均（卷积）滤波，中值滤波和高斯平滑
### 概率密度函数
![gaussian](/img/gaussian.bmp)
### 生成
```matlab
distI=imnoise(I,'gaussian',0.1);  %0.1为系数，调整噪声的强度，得到添加了高斯噪声的图像
```
### 对图像的干扰效果
![gaussian_f7](/img/gaussian_f7.bmp)

## 均匀分布噪声
### 定义
均匀分布噪声是指它的概率密度函数服从均匀分布的一类噪声。均匀分布是概率统计中的重要分布之一。顾名思义，均匀，表示可能性相等的含义。
### 概率密度函数
![balance](/img/balance.bmp)
### 生成
```matlab
Q=a+(b-a)*rand(m,n); % 得到均匀噪声
```
```matlab
for i=1:m
    for j=1:n
        I(i,j)=I(i,j)+Q(i,j); %将噪声添加到原图中
    end
end
```
### 对图像的干扰效果
以取值a=50，b=150为例：  
![balance_50_150](/img/balance_50_150.bmp)  
![balance50150](/img/balance50150.bmp)  

## 椒盐噪声
### 定义
椒盐噪声又称为脉冲噪声，它是非连续的，由持续时间短和幅度大的不规则脉冲或噪声尖峰组成。产生脉冲噪声的原因多种多样，其中包括电磁干扰以及通信系统的故障和缺陷，也可能在通信系统的电气开关和继电器改变状态时产生。
### 概率密度函数
![pepper](/img/saltpepper.bmp)
### 生成
椒盐噪声：  
```matlab
distI=imnoise(I,'salt & pepper',0.1);  %得到含椒盐噪声的图像
```  
椒噪声：  
```matlab
if (distI(i,j)==255 && I(i,j)~=255)
    distI(i,j)=0;
else
    distI(i,j)=distI(i,j);
end
```
盐噪声：  
```matlab
if (distI(i,j)==0 && I(i,j)~=0)
    distI(i,j)=255;
else
    distI(i,j)=distI(i,j);
end
```  

### 对图像的干扰效果
椒盐噪声：  
![add_saltpepper](/img/add_saltpepper.bmp)
盐噪声：  
![add_salt](/img/add_salt.bmp)
椒噪声：  
![add_pepper](/img/add_pepper.bmp)


---


# 10种典型滤波器  
本节将通过控制变量的实验方法，用不同的滤波器来分别过滤上述的三种噪声，探究不同滤波器滤除噪声的能力，
得出何种滤波器设置何参数时对于何种噪声的滤除效果最好的结论。
## 算数均值滤波
### 高斯噪声
### 均匀分布噪声
### 椒盐噪声

## 几何均值滤波
### 高斯噪声
### 均匀分布噪声
### 椒盐噪声

## 谐波均值滤波
### 高斯噪声
### 均匀分布噪声
### 椒盐噪声

## 逆谐波均值滤波
### 高斯噪声
### 均匀分布噪声
### 椒盐噪声

## 中值滤波器
### 高斯噪声
### 均匀分布噪声
### 椒盐噪声

## 最大值滤波器
### 高斯噪声
### 均匀分布噪声
### 椒盐噪声

## 最小值滤波器
### 高斯噪声
### 均匀分布噪声
### 椒盐噪声

## 中点滤波器
### 高斯噪声
### 均匀分布噪声
### 椒盐噪声

## 修正后的alpha均值滤波器
### 高斯噪声
### 均匀分布噪声
### 椒盐噪声

## 自适应中值滤波器
### 高斯噪声
### 均匀分布噪声
### 椒盐噪声

---
# 总结
# 参考文献
