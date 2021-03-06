ArCoreProject
==========

ARCore + Unity + MMD (MikuMikuDance) 实践  
**********

## 成果展示 ##  


<center>
    <img src="https://github.com/123lxw123/ArCoreProject/blob/master/source/part1.gif">
</center>  


<center>
    <img src="https://github.com/123lxw123/ArCoreProject/blob/master/source/part2.gif">
</center>


## 背景描述 ##

今年 Apple、Google 相继发布了自家的增强现实（AR）平台 ARKit、ARCore，大大降低了移动端 AR 开发门槛，AR 移动化也是未来的一个发展方向。恰好公司举办 Hackathon 活动，以 Hackathon 为契机对 ARCore 进行学习实践，并把实践的过程和遇到的问题整理记录下来。

>注意，由于目前这个 Android ARCore SDK 刚刚推出，Google 没有做太多设备的兼容，目前仅支持这些型号：Google Pixel 、 Google Pixel XL 、 Samsung Galaxy S8 (SM-G950U, SM-G950N, SM-G950FD, SM-G950FD, SM-G950W, SM-G950U1），并且 Android SDK 7.0 或更高版本。  

<center>
    <img src="https://diycode.b0.upaiyun.com/photo/2017/2574accef8d283da1ce2139673219d20.png">
</center>  

## 实践过程 ##

- 基础服务，调试手机(需要是以上支持的型号)安装 [arcore-preview.apk](https://github.com/google-ar/arcore-android-sdk/releases/download/sdk-preview/arcore-preview.apk) 作为一个基础服务，手机安装完后在应用程序里面会有一个 Tango Core 服务。开启开发者选项，并打开 USB 调试模式。

- 搭建开发环境，下载安装 [JDK](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)、[Android SDK(可通过 Android Studio 或者单独的 SDK Manager 安装)](https://developer.android.com/studio/index.html)、[Unity 最新 Beta 版](https://unity3d.com/cn/unity/beta?_ga=2.92421332.833162943.1512107097-1081327587.1507388747) (本环境 2017.3.0b4 版)。Unity 导入 ARCore SDK 项目(```git clone https://github.com/google-ar/arcore-unity-sdk.git```)，修改相关设置，参考 [Getting Started with Unity](https://developers.google.com/ar/develop/unity/getting-started)  
避坑：注意 Unity 是最新 Beta 版，而不是正式版  
<center>
    <img src="https://github.com/123lxw123/ArCoreProject/blob/master/source/init-arcore-project.png">
</center>  

<center>
    <img src="https://github.com/123lxw123/ArCoreProject/blob/master/source/build-settings.png">
</center>

- MMD4Mecanim 插件，Unity 导入插件 MMD4Mecanim (本环境 MMD4Mecanim_Beta_20150508)，参考 [Google ARCore 突破次元壁](https://zhuanlan.zhihu.com/p/29026662)  
避坑：需要老版的 MMD4Mecanim 插件，根据报错提示修改相关代码  

<center>
    <img src="https://github.com/123lxw123/ArCoreProject/blob/master/source/MMD4Mecanim.png">
</center>

- MMD 模型，Unity 导入 MMD 模型 生成 fbx 文件，参考 [手把手教你把 MMD 模型导进 Unity](http://www.bilibili.com/video/av3687730/)，切换模型 Rig 模式为 Lecagy  
避坑：Mac 上 Unity2017.3.0b4 版 + MMD4Mecanim_Beta20150508 导入 MMD 模型发现颜色明显不对劲，后来在 Windows 上 Unity5.3.2f1 版 + MMD4Mecanim_Beta20150508 导入完美，再导出成 unitypackage 便可导入 Mac Unity  

<center>
    <img src="https://github.com/123lxw123/ArCoreProject/blob/master/source/mmd.png">
</center>

- 声音，把 xxx.fbx 拖到 Scenes 中，右边菜单栏 Add Component > Audio > Audio Source，把声音文件拖到 AudioClip 中，左边菜单栏把 刚放进来的 MMD 模型重命名，再拖回原来的位置，这时会生成一个 xxx.prefab 文件，把生成的 xxx.fbx 文件拖动替换 ExampleController 中的 Andy Android Prefab，build & run  

<center> 
    <img src="https://github.com/123lxw123/ArCoreProject/blob/master/source/mmd-audio.png">
</center>  

<center>
    <img src="https://github.com/123lxw123/ArCoreProject/blob/master/source/mmd-replace.png">
</center>

- 阴影，首先添加光源，在 Scenes 左边菜单栏选中 Evironmental Light，Add Component > Rendering > Light，Type Diretional，Shadow Type Soft Shadows，Strength 调低一点，Resolution 选则 Very Hight Resolution，调整光源的位置。添加 [ARCoreUtils](https://github.com/jonas-johansson/ARCoreUtils)，把 Neustone 文件夹 放到项目 Assets 目录下，把 Neustone > ARCoreUtils 下 ARSurfaceManager.prefab 拖到 Scenes 中，build & run  
避坑：如果还是没出现阴影，注意调节光源的亮度和方向，可以尝试修改项目 MMD 文件夹中的 Materials 文件夹下素材的 Shader， 选中素材右边菜单栏 Shader 选择 ARCore > DiffusWithLightEstimateion，有些素材修改后模型可能显示异常，把不会异常的素材都修改成 DiffusWithLightEstimateion，build & run  

<center>
    <img src="https://github.com/123lxw123/ArCoreProject/blob/master/source/ARCoreUtil.png">
</center>  

<center>
    <img src="https://github.com/123lxw123/ArCoreProject/blob/master/source/materials-shader.png">
</center>

- 动态模糊，为了使模型在镜头移动过程中更接近现实效果，需要添加动态模糊的效果，参考 [PostProcessing Quickstart](https://github.com/Unity-Technologies/PostProcessing/wiki/(v2)-Quickstart)  
 
