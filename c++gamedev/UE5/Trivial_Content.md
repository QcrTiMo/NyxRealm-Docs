# 游戏事件

## 游戏模式

### **On Post Log In：**

玩家成功登录游戏后调用

### **Handle Starting New palyer：**

在On Post Log In调用后被调用，用来定义新进入的玩家会发生什么

### **SpawnDefaultPawnAtTransform：**

这个事件可以触发游戏中实际的pawn生成，新连接的玩家可以在特定的变换或在关卡中预设的玩家起始位置生成。

### **On Logout：**

玩家离开游戏的时候或者销毁的时候调用

### **On Restart player：**

调用该事件来让玩家重生，与SpawnDefaultPawnAtTransform类似，玩家可以在特定的变换或预先指定的位置重生

## 事件图表

### **Event Blueprint Initialize Animation：**

用处初始化动画

### **Event Blueprint Update Animation：**

每帧执行一次，允许开发人员执行计算并且更新其值