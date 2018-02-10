# 离屏渲染
* 使用OpenGL的帧缓冲（Frame Buffer）将场景渲染到不同的帧缓冲，可以做图像的后期处理；
* 使用多样本帧缓冲还可以实现抗锯齿（[Anti-aliasing](https://en.wikipedia.org/wiki/Anti-aliasing)）效果,称为离屏[MSAA](https://en.wikipedia.org/wiki/Multisample_anti-aliasing)，甚至可以自定义抗锯齿算法；

## 依赖
* glfw3.lib 推荐在[官方网站](http://www.glfw.org/download.html)下载源代码，然后自行编译。本项目编译使用的是CMake和Visual Studio 2015.
* GLAD 打开GLAD的[在线服务](http://glad.dav1d.de/)可轻松配置。本项目使用OpenGL 4.3.
* stb_image.h 是[Sean Barrett](https://github.com/nothings)的一个非常流行的单头文件图像加载库，可以在[这里](https://github.com/nothings/stb/blob/master/stb_image.h)下载。本项目使用其来加载纹理图片。
* GLM 一个只有头文件的库，不用链接和编译。可以在它们的[网站](http://glm.g-truc.net/0.9.5/index.html)上下载。本项目使用其作为数学库。
* Assimp 一个非常流行的模型导入库，可以在[下载页面](http://assimp.org/main_downloads.html)选择相应的版本，自行使用CMake 和 Visual Studio 2015编译。

## 后期处理
* 原始画面：
![Origin](https://github.com/SweeneyChoi/FBO-in-OpenGL/blob/master/images/origin.png)
* 反相(Inversion)：
![Inversion](https://github.com/SweeneyChoi/FBO-in-OpenGL/blob/master/images/reversion.png)
* 灰度化(Grayscale)：
![Grayscale](https://github.com/SweeneyChoi/FBO-in-OpenGL/blob/master/images/grayscale.png)
* 抗锯齿(Anti-aliasing):
* 抗锯齿比较特殊，使用**多采样抗锯齿(Multisample Anti-aliasing)**,意味着要使用多采样帧缓冲。一个多采样图像包含了比普通图像更多的信息，所以最后需要压缩或还原图像。如果想要使用AA后的图像做后期处理，还需要生成一个新的FBO作为中介。
![Anti-aliasing](https://github.com/SweeneyChoi/FBO-in-OpenGL/blob/master/images/anti-aliasing.png)
* 核效果（Kernel）：
#### 锐化(Sharpen):
![Sharpen](https://github.com/SweeneyChoi/FBO-in-OpenGL/blob/master/images/sharpen.png)
#### 模糊(Blur):
![Blur](https://github.com/SweeneyChoi/FBO-in-OpenGL/blob/master/images/blur.png)
#### 边缘检测(Edge-detection):
![Edge-detection](https://github.com/SweeneyChoi/FBO-in-OpenGL/blob/master/images/edge-detection.png)
