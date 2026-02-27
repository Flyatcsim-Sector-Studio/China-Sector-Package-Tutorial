# CSPR插件

CSPR Plugin

## 介绍

用于扇区内容绘制

## 自定义设置

1. ···\China_Sector_Package\Data\Plugins\China Sector Package Plugins\APT.json

  - 功能：存储机场的标高数据以计算五边延长线

  !!! Note
  	 注：该文件不推荐修改，添加、修改、删除的数据请符合json的格式要求，否则未知错误无法估计

2. ···\China_Sector_Package\Data\Plugins\China Sector Package Plugins\Color.json

  - 功能：用于存储绘制内容的颜色
  - 类别：
  	- Coastline：海岸线
  	- Taxiline：滑行线
  	- HoldingPoint：等待点文本
  	- HoldingPoint-Block：等待点文本的框
  	- HoldingPoint-Background：等待点文本的背景
  	- Grass：草坪
  	- TaxiwayBorder：滑行区域
  	- Buildings：建筑物
  	- RunwayBorder：跑道
  	- TaxiwayMark：滑行道标志
  	- Taxiout：滑出箭头
  	- Taxiin：滑入箭头
  	- Taxiall：通用箭头
  	- Close：关闭区域
  	- AIRSPACE：CTR边界
  	- HIGH：弃用
  	- TWR：TWR边界
  	- MVA：MVA边界
  	- APP：APP边界
  	- Taxiway：滑行道文本
  	- Taxiway-Block：滑行道文本的框
  	- Taxiway-Background：滑行道文本的背景
  	- Parking：机位文本
  	- Mark：地面标记
  	- Holding：等待线
  	- Inter：弃用
  	- RunwayMark：跑道的白块
  	- TaxiwayLimit：小滑行道区
  	- MARK：弃用
  	- RunwayMarkInside：跑道引进线
  	- Highway：高速公路
  	- GrassBorder：草坪边界
  	- Runway：跑道编号文本
  	- Runway-Block：跑道编号文本的框
  	- Runway-Background：跑道编号文本的背景
  	- Star：Star程序
  	- 3D-Light：3D高光边
  	- Hot：热点区域
  	- Transfer：移交信息文本
  	- Transfer-Block：移交信息文本的框
  	- Transfer-Background：移交信息文本的背景
  	- SOP：SOP文本

  - 格式：R，G，B，A
  	- R：红色的百分比
  	- G：绿色的百分比
  	- B：蓝色的百分比
  	- A：透明程度（0为看不到）


!!! Note
	 注：修改颜色请符合格式要求，否则未知错误无法估计
