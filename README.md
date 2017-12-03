ArCoreProject
==========

RrCore + Unity + MMD (MikuMikuDance) 实践
**********

1. 下载安装 [Unity 最新 Beta 版](https://unity3d.com/cn/unity/beta?_ga=2.92421332.833162943.1512107097-1081327587.1507388747) (本环境 2017.3.0b4 版)  
避坑：注意是最新 Beta 版，而不是正式版

2. 下载 ArCore SDK，使用 Unity 打开并修改相关设置，参考 [Getting Started with Unity](https://developers.google.com/ar/develop/unity/getting-started)

3. Unity 导入插件 MMD4Mecanim (本环境 MMD4Mecanim_Beta_20150508)，参考 [Google ARCore 突破次元壁](https://zhuanlan.zhihu.com/p/29026662)  
避坑：需要老版的 MMD4Mecanim 插件，根据报错提示修改相关代码

4. Unity 导入 MMD 模型，参考 [手把手教你把 MMD 模型导进 Unity](http://www.bilibili.com/video/av3687730/)  
避坑：Mac 上 Unity2017.3.0b4 版 + MMD4Mecanim_Beta20150508 导入 MMD 模型发现颜色明显不对劲，后来在 Windows 上 Unity5.3.2f1 版 + MMD4Mecanim_Beta20150508 导入完美，再导出成 unitypackage 便可导入 Mac Unity

5. 在 Unity 中打开 Assets > GoogleARCore > HelloARExample > Scenes，把第四步生成的 xxx.fbx 文件拖动替换 ExampleController 中的 Andy Android Prefab，build & run 不出意外就能成功把 Android 小机器人替换成 MMD 模型

6. 声音，把 xxx.fbx 拖到 Scenes 中，右边菜单栏 Add Component > Audio > Audio Source，把声音文件拖到 AudioClip 中，左边菜单栏把 刚放进来的 MMD 模型重命名，再拖回原来的位置，这时会生成一个 xxx.prefab 文件，把生成的 xxx.fbx 文件拖动替换 ExampleController 中的 Andy Android Prefab，build & run ，模型便会伴随音乐起舞

7. 阴影
