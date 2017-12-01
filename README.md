
#ArCoreProject#
#RrCore + Unity + MMD (MikuMikuDance) 实践
#折腾之路
1.下载安装 [Unity 最新 Beta 版](https://unity3d.com/cn/unity/beta?_ga=2.92421332.833162943.1512107097-1081327587.1507388747) (本环境 2017.3.0b4 版)
避坑：注意是最新 Beta 版，而不是正式版

2. Unity 导入插件 MMD4Mecanim (本环境 MMD4Mecanim_Beta_20150508)，参考 [Google ARCore 突破次元壁](https://zhuanlan.zhihu.com/p/29026662)
避坑：需要老版的 MMD4Mecanim 插件，根据报错提示修改相关代码

3.Unity 导入 MMD 模型，参考 [手把手教你把 MMD 模型导进 Unity](http://www.bilibili.com/video/av3687730/)
避坑：Mac 上 Unity_2017.3.0b4 版 + MMD4Mecanim_Beta_20150508 导入 MMD 模型发现颜色明显不对劲，后来在 Windows 上 Unity_5.3.2f1 版 + MMD4Mecanim_Beta_20150508 导入完美，再导出成 unitypackage 便可导入 Mac Unity

4.下载 ArCore SDK，使用 Unity 打开并修改相关设置，参考 [Getting Started with Unity](https://developers.google.com/ar/develop/unity/getting-started)

