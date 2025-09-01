
# AI对话


## 指令


### novel_ai绘图指令

```yaml
n4 prompt  #比如 n4 an anime girlish
n3 prompt  #比如 n3 an anime girlish
# 在prompt中随便一个地方加入横或方或竖就会变成画横图或方图或竖图，默认竖图
```


### sd绘图指令

```yaml
画 xxxxx
# 在prompt中随便一个地方加入横或方或竖就会变成画横图或方图或竖图，默认竖图
```


### tag反推

```yaml
tag
```
然后发送图片,或者引用图片使用。


### 重绘

```yaml
重绘 prompt   # 比如 重绘 1girl,solo,loli
n3re prompt  # nai3重绘
n4re prompt  # nai4重绘
# 在prompt中随便一个地方加入横或方或竖就会变成画横图或方图或竖图，默认自适应
# 在重绘的提示词内加入--left 114/--right 114/--left 114/--right 114这种语法会触发扩图，代表往哪个方向延展多少个像素
# 扩图状态下如果在提示词中包含--full，会对扩展后的图像进行全图重绘，而不仅仅是扩展部分重绘，一般来说衔接更好
```
然后发送图片,或者引用图片使用。


### 局部重绘

```yaml
局部重绘 prompt # sd局部重绘
# 在prompt中随便一个地方加入横或方或竖就会变成画横图或方图或竖图，默认自适应
```
然后先后发送图片和你蒙版过(用黑色覆盖你要重绘的地方)的图片,或者引用图片使用。


### 读原图的tag之类的各种参数信息

```yaml
imginfo
```
然后发送图片,或者引用图片使用。


### 指令设置参数（在后面还会讲到高级用法）

```yaml
setsd xxxx   #设置sd参数(比如setsd --w 1024 --h 1600就会把宽设为1024，高设为1600)（注意空格和"--"）
setre xxxx   #设置重绘参数
# 目前可用的参数:--w(宽，值要求为整数) --h(高，值要求为整数) --d(重绘幅度，0到1之间的小数) --p(正向提示词) --n(负面提示词)
# setsd 0或setre 0可以回到默认设置
# 注:优先级是关键词中含有横或方或竖最高，其次你自定义的分辨率，nai相关部分不受自定义分辨率影响，同时自定义横和宽不能超过1600
```


### 重绘中断指令
如果你在图片输入之前突然不想要重绘了，可以发送这条指令

```yaml
/clearre
```


### 查询指令

```yaml
lora
ckpt
scheduler
sampler
```


### 切换模型

```yaml
ckpt2 {modelname}
```


### 查询danbooru词条

```yaml
dan {你要查的tag，可以是各种语言}
```


### 获取抽卡可用词条(具体用法后面会讲)

```yaml
getwd
```


## 进阶用法

### 函数调用
画图可以使用`【函数调用】`，直接告诉bot要绘制的内容。


### 关于抽卡（wildcard）功能

```yaml
getwd # 可以获得所有能够抽取的wildcard
getwd xxx # 你给一串提示词，还给你抽卡处理过后的句子
```

:::warning
注意：后面的wd指令是当作提示词用的
:::

```yaml
<wda:x=y>
```
此指令会固定从名为x的wildcard中抽取y项，附加a的固定权重
```yaml
<wda-b:x=y>
```
此指令会从名为x的wildcard中抽取y项，附加a到b范围内的随机权重 如果权重参数（a-b或a）出现问题，默认为权重范围0到1
举例:
```yaml
画 1girl,<wd1:artist=1> # 随机抽一个画师，权重为1，例如wlop
画 1girl,<wd1:artist=2> # 随机抽两个画师，权重为1，例如wlop,torino aqua
画 1girl,<wd0.5:artist=2> # 随机抽两个画师，权重为0.5，例如(wlop:0.5),(torino aqua:0.5)
画 1girl,<wd0.4-0.5:artist=3> # 随机抽3个画师，权重为0.4到0.5中的随机数，例如(a:0.4111),(b:0.4231),(c:0.4342)
画 1girl,<wd1:artist=2>,<wd0.6:artist=3> # 随机抽五个画师，两个权重为1，三个权重为0.6
```


### setsd和setre的参数重设
基础的这里就不讲了，这里是一些进阶用法

注意nai部分也可使用setsd和setre调整参数，只有分辨率不受影响

接下来以setsd为例，setre同理

重置指定项指令
```yaml
setsd --w 1024 --h
```
这里的--h后面没有定义值，所以高度会被重置回默认值

重设正面或负面提示词
```yaml
setsd --p masterpiece,best quality,amazing quality,very aesthetic,absurdres,newest,
```
这上面的会把默认正面提示词设为masterpiece,best quality,amazing quality,very aesthetic,absurdres,newest,然后你以后每次画画的词加在这句话的前面

但是我们有时候不想要输入的词在句首，那么我们可以用一个空的大括号来表示你之后输入的词插入的位置
```yaml
setsd --p masterpiece,{},best quality,{},amazing quality,very aesthetic,absurdres,newest,
```
在上面的例子里，我们在两个地方插入了大括号

那么接下来，假设你使用了"画 1girl"

实际上的整句话就是
```yaml
masterpiece,1girl,best quality,1girl,amazing quality,very aesthetic,absurdres,newest,
```
注意，setsd和setre中的--p和--n参数可以处理wildcard，所以可以在setsd和setre指令中出现wildcard语法，从而达到每次画图都抽卡的效果



