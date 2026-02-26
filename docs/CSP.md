# CSP插件

CSP Plugin

## 介绍

用于扇区内Tag、List、自定义绘制的一个插件

## 显示项目介绍（Tag Item type）

1. COPN

	- 功能：用于显示进入扇区的移交点
	- 显示：`XXXXX*`
		- `XXXXX`：移交点的名称
		- `*`：有更多内容
	- 用处：Sector Inbound List 的 COPN

2. COPX

	- 功能：用于显示离开扇区的移交点
	- 显示：`XXXXX*`
		- `XXXXX`：移交点的名称
		- `*`：有更多内容
	- 用处：Sector Exit List 的 COPX

3. DES

	- 功能：显示距离计算的下高的距离
	- 显示：XXX
		- XXX：纯数字
		- 单位：nm
	- 用处：Sector Exit List 的 TD

4. Equiptment

	- 功能：显示机组飞行计划填写的航空器性能

	- 显示：

		|	 代码	 |								 类型									|
		| :--------: | :---------------------------------------------------: |
		|		X		|				没有进入RVSM空域能力和RNAV1能力				|
		|		W		|						没有进入RVSM空域能力						|
		|		R		|							没有RNAV1能力							|
		|		R*		| 机载设备有RNAV1能力，PBN类型未填写支持RNAV1（D1，D2） |
		| A（绿色）	|			机载设备能执行RNP程序，包括执行RF航段			|
		| A*（绿色） |			机载设备能执行RNP程序，但不包括RF航段			|

	- 用处：Departure List 的 EQ 和 Startup List 的 EQ 和 Tag 的 EQ

5. FPC

	- 功能：检查飞行计划
	- 显示：`XXXX*`
		- `XXXX`：错误类型
		- `*`：有 **≥1** 个错误
		- 类型：
		- ALT：巡航高度不正确（根据起飞和落地机场的经度进行匹配）
		- ADEP/ADES：起飞/落地机场不在数据库
		- VFR：计划：VFR
		- TYPE：航空器机型不在数据库中
		- PBN：PBN代码未填写/缺少性能（/TEXT：未填写PBN代码，/RNAV：填写的PBN代码不具备RNAV1能力）
		- ACEQ：设备代码的未填写
		- ROTE：航路不在数据库
	- 用处：Departure List 的 FPC

6. Inticial Altitude

	- 功能：显示起始高度
	- 显示：XXXX
		- XXXX：纯数字
		- 单位：百米
		- 颜色：
		 - 白色：根据已选择的起始高度匹配到高度但**未确认**
		 - 与其他项目同色：**已确认**
	- 用处：Departure List 的 CFL

7. Language Indicator

	- 功能：显示机组的特殊语言类型
	- 显示：EN/CN
	- 用处：Sector Inbound List 的 LG 和 Sector Exit List 的 LG 和 Departure List 的 LG 和 Startup List 的 LG 和 Tag 的 LG

8. LID Indicator

	- 功能：显示机组是否接收到了LID
	- 显示：▉
		- 颜色：
		 - 红色：未发送
		 - 绿色：已发送
	- 用处：Sector Exit List 的 LI

9. On Request

	- 功能：机组申请的项目
	- 显示：CLX/PUX
		- X：纯数字
		- CL：放行
		- PU：推出
	- 用处：Departure List 的 # 和 Startup List 的 #

10. Origin Error Indicator

	 - 功能：显示出发机场错误
	 - 显示：*/空
		- *：出发机场不存在
	 - 用处：FP List 的 第一项（空）

11. SIE

	 - 功能：显示飞行航路中的离场点
	 - 显示：XXXXX
		- XXXXX：点的名称
	 - 用处：Departure List 的 SIE 和 Startup List 的 SIE

12. SLOT

	 - 弃用

13. STAR

	 - 功能：显示飞行航路中的STAR程序
	 - 显示：XXXXX*
		- XXXXX：程序名称
		- *：还有更多信息
	 - 用处：Sector Exit List 的 STAR

14. STE

	 - 功能：显示飞行航路中的进场点
	 - 显示：XXXXX
		- XXXXX：点的名称
	 - 用处：Sector Exit List 的 STE

15. Tag Line 3 Item

	 - 功能：显示Tag的第三行的内容
	 - 显示：AAAA BBBB / XXXXX XXXXX （每两秒改变一次）
		- AAAA：落地机场
		- BBBB：机型类型
		- XXXXX XXXXX：下两个点的名称
	 - 用处：Tag 的 第三行

## 左右键功能介绍

1. Auto Delivery

	- 功能：自动放行

	- 运行流程：（以下所写的发送均在AutoDelivery中以选择的机组呼号发送）

		1. 检查是否启用了机组起飞机场的跑道

			若无将发送```Please set the active departure runway at XXXX(机场)```

		2. 检查是否：多跑道可用

			若：多跑道运行，且未确认跑道将发送```There are more than one runway is avilible. Please set the runway firstly.```

		3. 检查是否有SID匹配

			若无SID匹配将发送```There is no SID avalible for the aircraft. Please check its route firstly.```

		4. 检查是否有先前设置过的起高

			若无先前发送过的起始高度将发送```Please set a model intial altitude for the runway.```

		5. 均无问题后，将自动确认跑道、SID、CFL、分配ASSR

	- 用处：FPC 的 右键

2. Find Currect Aircraft Position

	- 功能：寻找机组位置
	- 运行流程：以机组：中心画一个圆，3秒后自动消失
	- 用处：TYPE 的 右键

3. Open Descent alt edit

	- 功能：选择一个点到达并输入高度以启用TD计算
	- 运行流程：
		1. 打开一个未来航路点的列表
		2. 待选择了一个航路点后，出现一个输入框以输入高度（百米，6000m->60）
		3. 启用**同一个航路点，同一个落地机场**的机组的TD计算
	- 用处：TD 的 左键

4. Open Request List

	- 功能：打开选择机组申请的类型
	- 运行流程：打开一个申请类型的列表进行选择
	- 用处：# 的 左键

5. Send LID Message

	- 功能：发送LID信息

	- 运行流程：

		1. 检查STAR、ARWY是否确认

			若有问题将显示在LIDAutoSender中发送```请先设置 XXXX```

		2. 自动发送LID的私聊信息给对应机组

			```NO NEED TO REPLY THIS MSG*** THIS IS LID (LANDING INFORMATION DELIVER) FOR CALLSIGN, EXPECT {} ARRIVAL RWY XX TO XXXX. ON INITIAL CONTACT APPROACH, PILOT ONLY NEED TO REPORT DETAILED STAR AND RWY RECEIVED BY LID.```

	- 用处：LI 的 左键

6. Set Inticial Altitude

	- 功能：设置起始高度
	- 运行流程：打开一个高度选择列表进行选择
	- 用处：CFL 的 右键

	!!! Note
		 注：这会将同一跑道、同一起飞机场的机组均预设置：该起始高度

7. Set Inticial Altitude / Comfirm Initicial Altitude

	- 功能：设置起始高度 / 确认起始高度
	- 运行流程：
		1. 若有预设的起始高度则**确认起始高度**
		2. 反则，打开一个高度选择列表进行选择
	- 用处：CFL 的 左键

8. Show Copn Full Name

	- 功能：显示Copn的全部信息
	- 运行流程：出现一个列表以显示整个Copn的内容，通常包括移交高度信息
	- 用处：Copn 的 左键

9. Show Copx Full Name

	- 功能：显示Copx的全部信息
	- 运行流程：出现一个列表以显示整个Copx的内容，通常包括移交高度信息
	- 用处：Copx 的 左键

10. Show Flight Plan Check Info

	 - 功能：显示飞行计划检查的全部错误
	 - 运行流程：出现一个列表以显示一个列表以查看全部的错误
	 - 用处：FPC 的 左键

11. Show Star Full Name

	 - 功能：显示Star的全部信息
	 - 运行流程：出现一个列表以整个Star的内容，可能包含有ILS-Y、ILS-X等信息，默认：ILS-Z
	 - 用处：Star 的 右键

12. Toggle Historical Route

	 - 功能：显示机组的历史航迹
	 - 运行流程：在雷达屏幕上绘制机组的开始出现在雷达屏幕上后的航迹
	 - 用处：ASSR 的 右键

## DRAW LINE 按钮

- 功能：让管制员可以在雷达屏幕上绘制自定义的多边形

- 运行流程：

	1. 左键点击**按钮**以开始在屏幕上绘制
	2. 点击屏幕上的多个点 ······
	3. （中键点击**按钮**撤回上一个点）
	4. 右键点击**屏幕**以结束绘制，将自动连成一个多边形
	5. （右键点击**按钮**删除上一个保存的多边形）

	!!! Note
		注：（可选操作）

## 自定义设置

1. ···\China_Sector_Package\Data\Plugins\China Sector Package Plugins\CSP-Settings.json

	- Replace-auth-address：EuroScope-jwt-auth替换的地址（空：Vatsim）

	- Color-：

		- Notice：FPC检查错误的颜色
		- Star：Star项的颜色
		- COPX：COPX项的颜色
		- COPN：COPN项的颜色
		- Prepared：预选项的颜色（CFL）
		- Confirmed：确认后项的颜色

		!!! Note
			注：修改后需要重启EuroScope才能生效

2. ···\China_Sector_Package\Data\Plugins\China Sector Package Plugins\wingspan.json

	- Aircraft：机型对应的翼展数据（不推荐修改）
	- Airport：机场的机位的最大容纳翼展限制（可根据需求自主添加）

!!! Note
	 注：添加、修改、删除的数据请符合json的格式要求，否则未知错误无法估计
