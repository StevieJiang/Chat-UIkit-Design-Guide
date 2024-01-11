# 直播聊天室人机交互界面工具包设计指南 (V1.0.0)
Design Guide of Live Stream Chat UIkit(Beta)

<img src="https://s2.loli.net/2024/01/02/s5aIcuCmEoZx1yM.png" width="100%" >

## 0.总的设计原则

### 0.1.功能与行为上确保通用、普遍、一般

### 0.2.风格上易于自定义

### 0.3.在业务形态上尽量不替用户做决定

## 1.全局样式（Style）

### 1.1.UIkit 色彩规范

#### 1.1.1.颜色配置说明：

##### 1.1.1.1.颜色类（Color Class）

一般颜色类分为八类：
主题色（Theme Color）：Primary、 Secondary、Error 三类；
渐变主题色（Primary Gradient）一类（含 8 种）；
透明色（Alpha Color）：On Light、On Dark 两类；
中性色（Neutral Colors）：Neutral、Neutral Special 两类；

##### 1.1.1.2.颜色模式（Hsla Model）

颜色模式为比较直观的 hsla 模式:
整个模型是一个圆柱体，圆柱体底面周长划分为 360°，对应不同的色相（Hue）;
圆柱体的半径为饱和度（Saturation），圆心为 0（最灰），半径值为 100（最艳）；
圆柱体的高为亮度（Lightness），起始点为 0（纯黑色），中心点是 50(标准色,)，结束点为 100(纯白色)。

##### 1.1.1.3.模型概览：

<img src="https://s2.loli.net/2024/01/02/1XfpZuKaNBD26GW.png" width="600" >

#### 1.1.2.三种主题色（Theme Color）的色彩规范：

##### 1.1.2.1.关于用户可配项（Hue value）：

用户可设定颜色类的可配项 Hue(0-360)为任意数值，修改后每类颜色的色相会发生变化，以贴合用户场景所需要的主题颜色。
Hue 值(0-360)与色相的对应关系大致如以下图示所例：

<img src="https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk11211.png" width="600" >

用户可依据自身产品的品牌色指定色相数值（Hue），从而确认主题色 Primary（主要用于 UI 组件中关键操作与重要文本展示，如推荐的 action、高亮显示的文本等），以及用于积极提示的 Secondary，和表示警示提示的 Error。

<img src="https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk11212.png" width="600" >

##### 1.1.2.2.关于饱和度（Saturation value）:

饱和度(Saturation)不开放给用户设置，三种主题色 Primary、 Secondary、Error 默认饱和度为 100%，Neutral 默认为 8%，Neutral Special 默认为 36%

<img src="https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk1122.png" width="600" >

##### 1.1.2.3.关于亮度级别（Lightness level）:

亮度(Lightness)百分比用户不可随意设置，每个颜色类提供：0(0%) / 1(10%) / 2(20%) / 3(30%) / 4(40%) / 5(50%) / 6(60%) / 7(70%) / 8(80%) / 9(90%) / 95(95%) / 98(98%) / 100(100%)十三个级别供用户可选；

<img src="https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk1123.png" width="600" >

##### 1.1.2.4.举个例子吧：

如指定主题色 Primary 色相（Hue）为 203，成功色 Secondary 色相（Hue）为 155，警示色 Error 色相（Hue）为 350，则会生成如下 39 种主题色可供用户在指定 UI 件块（View）颜色时使用：

<img src="https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk1124.png" width="800" >

其中，主题色 Primary 的 L5 为亮色模式下的基色（Key Color），L6 为暗色模式下的基色（Key Color）。所有的颜色体系都是依照基色生成。

#### 1.1.3.关于渐变主题色(Primary Gradient)的规范：

渐变主题色是由 Primary 色派生出的渐变色，为线性渐变(Linar Gradient)，渐变方向依图示坐标系分为 8 类：

<img src="https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk113.png" width="800" >

##### 1.1.3.1.关于渐变色的起始色(Start Color)：

渐变色中 Start Color 规则和 Primary 类的色值保持一致;

<img src="https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk1131.png" width="800" >

##### 1.1.3.2.关于渐变色的结束色(End Color)：

End Color 用户可配置色相（Hue），亮度以 0(20%) / 1(30%) / 2(40%) / 3(50%) / 4(60%) / 5(70%) / 6(75%) / 7(80%) / 8(85%) / 9(90%) / 95(95%) / 98(98%) / 100(100%)（对应 Primary 的 13 级亮度梯度值）为固定梯度值

以下以 Hue：233 为例，按照 End Color 颜色公式依旧得到 13 级颜色：

<img src="https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk11321.png" width="800" >

起始色和结束色结合，得到相应的渐变结果

<img src="https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk11322.png" width="800" >

##### 1.1.3.3.关于渐变主题色可配项(End Color Hue Value)：

用户仅可配置渐变色中 End Color 的色相（Hue）以达成与用户业务场景符合的渐变颜色效果；

##### 1.1.3.4.举个例子吧:

用户设置 End Color Hue = 233，选择渐变方向为“↓”，则可得到如下效果：

<img src="https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk11341.png" width="800" >

如使用渐变主题色，那么它将替代掉所有应用于背景色的 Primary 色

<img src="https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk11342.png" width="600" >

但一般不替代 UI 件块的前景色，因为没有什么意义，且有干扰文字阅读的可能性

<img src="https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk11343.png" width="600" >

#### 1.1.4.关于透明色(Alpha)的规范：

##### 1.1.4.1.透明色（Alpha Color）:

在本案内带有透明度的组件仅有弹幕消息背景色、礼物消息背景色、模态背景色、轻提示背景色四种，应用范围有限，所以单独定义两个特殊的颜色类用于以上四种组件：Alpha onlight(hsl0, 0%, 0%) 和 Alpha ondark(hsl0, 0%, 100%)，Alpha 值被指定为 0(0.0) / 1(0.1) / 2(0.2) / 3(0.3) / 4(0.4) / 5(0.5) / 6(0.6) / 7(0.7) / 8(0.8) / 9(0.9) / 95(0.95) / 98(0.98) / 100(1.0) 十三个梯度值，共 26 种颜色用例，以调整组件的背景色透明度。

<img src="https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk1141.png" width="800" >

Alpha onlight 和 Alpha ondark 均为默认值，无任何可配置项。

### 1.1.5.关于中性色（Neutral Colors）：

#### 1.1.5.1.中性色（Neutral）

中性色(Neutral)仅有一个可配项：色相（Hue），饱和度(Saturation)固定值为 8，亮度级别（Lightness level）也和主题色相同，分为 0(0%) / 1(10%) / 2(20%) / 3(30%) / 4(40%) / 5(50%) / 6(60%) / 7(70%) / 8(80%) / 9(90%) / 95(95%) / 98(98%) / 100(100%)十三个级别供用户可选；

<img src="https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk1151.png" width="600" >

Neutral 和 Primary 的默认 Hue 值(色相)相同，也建议用户设置和主题色相同的 Hue 值已达成主题颜色和无彩色系的配套。但这仅仅是建议；

#### 1.1.5.2.举个例子吧：

如指定主题色 Primary 色相（Hue）为 203，饱和度(Saturation)固定值为 100%，中性色（Neutral）则也指定色相（Hue）为 203，饱和度(Saturation)固定值为 8%，则得到以下色列可供用户选择使用：

<img src="https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk11521.png" width="800" >

其中，L98 为亮色模式下背景色的主色，L1 为亮色模式下前景色的主色；L1 为暗色模式下背景色的主色，L98 为暗色模式下前景色的主色。

<img src="https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk11522.png" width="800" >

### 1.1.6.关于特殊中性色（Neutral Special）：

特殊中性色 Neutral Special 主要用于级别低于 Primary 和 Secondary 的强调信息，如当前页面状态、消息发送者的昵称等。
Neutral Special 和 Primary 的默认 Hue 值(色相)类似，为近似色，也建议用户设置和主题色近似的 Hue 值已达成主题色和无彩色系的配套。但这仅仅是建议；

<img src="https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk116a.png" width="600" >

<img src="https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk116b.png" width="600" >

#### 1.1.6.1.举个例子吧：

如指定主题色 Primary 色相（Hue）为 203，特殊中性色（Neutral）通过相似色原理（正负 30 度内）指定色相（Hue）为 220，饱和度(Saturation)固定值为 36%，则得到以下色列可供用户选择使用：

<img src="https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk1161.png" width="800" >

## 1.2.主题

本期主题分为 2 种，每种分明亮（Light mode）和黑暗（Dark）两类。

### 1.2.1.圆润主题

组件一般采用较大的圆角，柔和轻盈

![image text](https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk121.png)

### 1.2.2.硬朗主题

组件一般避免比较大的圆，硬朗实在

![image text](https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk122.png)

以上两种主题可通过应用渐变主题色（Primary Gradient）得到两外两种渐变色主题。
至于业务相关的主题，如“社交”、“游戏”、“教育”、“商务”等主题分类，因违反本案的最基本设计原则“在业务形态上尽量不替用户做决定”，所以不在本期考虑范围内。

## 1.3.图标（Icon）

### 1.3.1.图标模板（Template）

图标参照 Material Icon Font 的模板 ，以 24 为基本栅格，须在安全区域(20x20 的中心区域)内绘制，基本描边控制为 1.5 栅格。

![image text](https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk131.png)

### 1.3.2 图标命名（Name）

为防止将图标语意固定，icon 命名需要尽力避免定义操作行为，而是以“看见什么就是什么“进行命名，方便相同图标在不同操作行为下的复用。
如

![image text](https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk132.png)

## 1.4.字体（Typography）

### 1.4.1.字族（Font Family）

#### 1.4.1.1.iOS 字族

默认 SF Pro 为基本西文（拉丁字母、希腊字母、西里尔字母等）字体；
默认 SF Arabic、SF Hebrew 等为基本右向左（Dextral-sinistral）文字字体；
默认苹方（PingFang SC、TC、HK）为中文（简体中文、繁体中文、香港繁体中文）字体；

#### 1.4.1.2.Android 字族

默认 Roboto 为基本西文（拉丁字母、希腊字母、西里尔字母等）字体；
默认 Noto Sans Arabic、Noto Sans Hebrew 等为基本右向左（Dextral-sinistral）文字字体；
默认思源黑体（Noto Sans SC、TC、HK）为中文（简体中文、繁体中文、香港繁体中文）字体；

#### 1.4.1.3.Web 字族

默认 Roboto 为基本西文（拉丁字母、希腊字母、西里尔字母等）字体；
默认 Noto Sans Arabic、Noto Sans Hebrew 等为基本右向左（Dextral-sinistral）文字字体；
默认思源黑体（Noto Sans SC、TC、HK）为中文（简体中文、繁体中文、香港繁体中文）字体；

### 1.4.2.字号（Font Size）

#### 1.4.2.1.最小字号

移动端最小字号为：11；web 端最小字号为：12

#### 1.4.2.2.字号规则

除移动端最小字号外，字号以 2 为梯度递增：
11，12，14，16，18，20

### 1.4.3.字重（Font Weight）

字重分为标准（Regular, 400）、中等（Medium,510）、加粗（semibold,590）三种；
在一些跨平台框架中，如遇不支持设置非百位整数字重，则取近似值百位整数；
如字族没有 semibold，则以 bold 替换。

### 1.4.4.行高（Line height）

行高依照以下固定值（字号/行高）：
11/14，12/16，14/20，16/22，18/26，20/28。

### 1.4.5.字体角色（Font Role）

字体角色分为 3 类：
大标题 Headline、标题 Title、标签 Label、正文 Body
需要注意的是，这些角色只是推荐的角色指示，并不具有完全的指定性，具体使用什么角色的字体需依照所使用的组件的实际情况（组件内信息的层级重要性，越重要的越大越重）而使用。

### 1.4.6.字体 Token

依照依照 4.1-4.5 规则，设定以下西文字体排版 token，

![image text](https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk146a.png)

简体中文字体 token 示意

![image text](https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk146b.png)

## 1.5.效果（Effects）

所应用的效果主要分为两种：背景模糊（Backround Blur）和阴影（Shadow）

### 1.5.1.背景模糊（Backround Blur）

背景模糊主要应用于组件背景色使用 Alpha color 时，如组件背景色的透明度会造成组件前后层级干扰的话，则推荐使用背景模糊解决，比如：

![image text](https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk151.png)

也应用于模态显示的弹出层的背景虚化；
背景模糊的模糊半径值默认为 20

```
/* bg_blur_modal */ backdrop-filter: blur(20);
```

### 1.5.2.阴影（Shadow）

阴影应用于弹窗（Alert）、浮层（pop）、抽屉（Drawer）等，为区分层级，凸显聚焦的组件。

#### 1.5.2.1.阴影型号（Size）

阴影分为小（small）、中(medium)、大(Large)三种型号，应用于不同尺寸的组件中，总体原则为：越小的组件越推荐使用小的阴影、反之越大的组件推荐使用大的阴影；圆角越小的组件越推荐使用小的阴影、反之亦然。

#### 1.5.2.2.阴影 token

为保证阴影效果自然柔和，每个阴影都有两层不同偏移、不同模糊度、不同透明度的值。同时针对亮色/暗色模式有两套不同颜色的阴影。

**Shadow on Light:**

```
/* shadow/onlight/large */
box-shadow: x0 y24 blur36 color(Neutral3) Alpha0.15, x8 y0 blur24 color(Neutral1) Alpha0.1

/* shadow/onlight/medium */
box-shadow: x0 y4 blur4 color(Neutral3) Alpha0.15, x2 y0 blur8  color(Neutral1) Alpha0.1

/* shadow/onlight/small */
box-shadow: x0 y1 blur3 color(Neutral3) Alpha0.15, x1 y0 blur2  color(Neutral1) Alpha0.1
```

![image text](https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk1522a.png)

**Shadow on Dark:**

```
/* shadow/onlight/large */
box-shadow: x0 y24 blur36 color(Neutral4) Alpha0.15, x8 y0 blur24 color(Neutral1) Alpha0.1

/* shadow/onlight/medium */
box-shadow: x0 y4 blur4 color(Neutral4) Alpha0.15, x2 y0 blur8  color(Neutral1) Alpha0.1

/* shadow/onlight/small */
box-shadow: x0 y1 blur3 color(Neutral4) Alpha0.15, x1 y0 blur2  color(Neutral1) Alpha0.1
```

![image text](https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk1522b.png)

## 1.6.圆角（Radius）

### 1.6.1.一般圆角

一般圆角分为 None（r=0）、Extra Small（r=4）、Small（r=8）、Medium（r=12）、Large（r=16）、Extra Large（r=½ Height）六个枚举值，
一般情况下组件的四个圆角为同一值

![image text](https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk161.png)

#### 1.6.1.1.Extra Small（r=4）

通常适用于如下组件
Button(Small Radius)
Input(Small Radius)
Float(Small Radius)
Message Bubble(Small Radius)
Avatar(Small Radius)
Popover
Global Broadcast(Small Radius)

#### 1.6.1.2.Small（r=8）

通常适用于如下组件
Alert(Small Radius)
Drawer(Small Radius)

#### 1.6.1.3.Medium（r=12）

通常适用于如下组件
本案暂不涉及

#### 1.6.1.4.Large（r=16）

通常适用于如下组件
Input Area(Large Radius)
Alert(Large Radius)
Drawer(Large Radius)
Float(Large Radius)

#### 1.6.1.5. Extra Large（r=½ Height）

通常适用于如下组件
Input Area(Large Radius)
Alert(Large Radius)
Drawer(Large Radius)
Message Bubble(Large Radius)

### 1.6.2.特殊圆角

特殊圆角应用于有背景色的 IM 聊天消息组件：
Message Bubble(Large Radius)

![image text](https://raw.githubusercontent.com/StevieJiang/Chatroom-UIkit-Design-Guide/main/Doc%20Image/cruk162.png)
