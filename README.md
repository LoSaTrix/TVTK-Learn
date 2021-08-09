# TVTK-Learn
# TVTK库 学习
代码文件见 **桌面/Python/tvtk** 文件夹

## 学习内容
1. TVTK：科学计算三维可视化、流水线模型、数据加载
2. Mayavi：三维网格面绘制、三维标量场和矢量场绘制
3. TraitsUI：交互式三维可视化
4. Scipy*：拟合、线性代数、统计、插值等

> Visualization is the sight of Data!

## 编程环境
模块    |课程选用版本 |使用版本
--      |:--:       |--:
Python  |3.6        |3.9.6
VTK     |7.1.1      |9.0.3
Mayavi  |4.5.0      |4.7.3
numpy   |1.11.3     |1.21.1
PyQt    |4.11.4     |5.15.4
Traits  |4.6.0      |6.2.0
TraitsUI|5.1.0      |7.2.1

## 安装组件推荐
+ Python 3.6
+ VTK-7.1.1-cp36-cp36m-win_amd64.whl
+ traits-4.6.0-cp36-cp36m-win_amd64.whl
+ mayavi-4.5.0+vtk71-cp36-cp36m-win_amd64.whl
+ PyQt4-4.11.4-cp36-cp36m-win_amd64.whl

## 代码文档
+ VTK官网文档：[VTK官网](http://www.vtk.org/doc/nightly/html/annotated.html)
+ mayavi官网文档：[mayavi官网](http://code.enthought.com/projects/mayavi/)
+ tvtk代码文档：`tvtk.tools.tvtk_doc.main()`

## 课程内容实例
1. 流体数据的标量可视化实例、矢量可视化实例
2. 三维扫描数据（模型/地形）可视化实例
3. 三维地球场景可视化实例
4. 曲线UI交互控制可视化实例

## 科学计算可视化主要方法
1. 二维标量数据场
   1. 颜色映射法
   2. 等值线方法
   3. 立体图法和层次分割法
2. 三维标量数据场
   1. 面绘制法
   2. 体绘制法
3. 矢量数据场
   1. 直接法
   2. 流线法

## 显示构建流程 -> 管线（pipeline）
1. 创建数据源
2. 将数据源转换为图形数据
3. 利用图形数据创建Actor角色
4. 创建Renderer渲染器，添加Actor角色组
5. 创建RenderWindow渲染窗口，添加Renderer渲染器组
6. 创建窗口交互工具并开启交互

## 管线技术（pipeline，流水线）
1. 可视化管线：将原始数据加工成图形数据的过程
   TVTK|说明
   --|--
   CubeSource|通过程序内部计算输出一组描述长方体的数据（PolyData）
   PolyDataMapper|PolyData通过该映射器将数据映射为图形数据（mapper）
2. 图形管线：将图形数据加工为我们所看到的图像的过程
   TVTK|说明
   --|--
   Actor|场景中的一个实体。它包括一个图形数据（mapper），具有描述该实体的位置、方向、大小的属性。
   Renderer|渲染的场景。它包括多个需要渲染的Actor。
   RenderWindow|渲染用的图形窗口，它包括一个或者多个Render。
   RenderWindowInteractor|给图形窗口提供一些用户交互功能，例如平移、旋转、放大缩小。这些交互式操作并不改变Actor或者图形数据的属性，只是调整场景中照相机（Camera）的一些设置。
![pipeline](../fig/pipeline.png)


## 函数记录
1. tvtk_doc.main()：代码文档（Python 3.9.6 打不开）
2. CubeSource()：立方体数据源
   1. 属性
      1. x/y/z_length：立方体在三轴方向上的长度
      2. center：立方体的中心坐标
      3. output_points_precision：立方体的精度
   2. 方法
      1. set/get_x/y/z_length()：设置/获取立方体在三轴方向上的长度（Python 3.9.6 不适用）
      2. set/get_center()：设置/获取立方体所在坐标系的原点（Python 3.9.6 不适用）
      3. set/get_bounds()：设置/获取立方体的包围盒
3. ConeSource()：圆锥数据源
   1. 属性
      1. height：圆锥的高度
      2. radius：圆锥底面半径
      3. resolution：圆锥底面的分辨率（n边形近似圆）
      4. center：圆锥的中心坐标
      5. Direction：圆锥底面的法线方向
4. CylinderSource()：圆柱数据源
5. ArcSource()：圆弧数据源
6. ArrowSource()：箭头数据源
