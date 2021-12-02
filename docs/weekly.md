# 周报

## 2021/12/2
> + 增加一个时间戳tween用来替换队伍移动时的tween,用于和时刻紧密相关的动效  
	用法类似于DOTween，新建完`TimeStampTween`或`TimeStampSequence`并填完相关参数后需要`TimeStampTweenUtil.Ins.AddSequence` `TimeStampTweenUtil.Ins.AddTween`添加之后开始生效
> + 修改了之前demo期的场景加载，现在的场景可以保留大地图和城内的gameobject，同一位置的切换消耗更少。  
	因为同时保留两张图，原来的`TeamMoveController`和`BuildingPlaceController`可能同时存在多个，不再使用Ins来调用，改为从顶部的`MapController`中的`WorldSceneController`里获取相应的Controller
	现在的场景结构：
	```
	└── MapController
	    └── WorldSceneController
		    ├── TerrainLoad
		    ├── TeamMoveController
		    ├── BuildingPlaceController
		    └── MapCityController
	```
	父节点会有子节点引用，子节点也会有父节点引用，方便数据传导  
> + 增加了`MapCityController`，和`BuildingPlaceController`类似用来管理大地图上主城的生命周期，将来可能会加入副本之类的
