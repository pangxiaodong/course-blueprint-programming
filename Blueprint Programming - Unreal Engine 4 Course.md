# Blueprint Programming - Unreal Engine 4 Course

https://www.youtube.com/playlist?list=PLL0cLF8gjBpqRUy7r0DtVY3Fcdgq5Wk-h

### **1.Programming Games With NO CODE**

### **2.Blueprints Interface Introduction**

  场景蓝图只能控制自己场景内的对象，不能控制其他场景内的对象。

  Actor蓝图：会有一个视口，Scene蓝图：不会打开一个视口。

### **3.Programming Concepts**

  Event -> Action -> Object

<img src="_IMG\Event-Action-Object.png"  style="zoom:75">

在场景中选中点光源，在Level蓝图里面，可以添加点光源的引用

<img src="_IMG\Create-a-Reference-to-PointLight.png"  style="zoom:0">

在Level蓝图里面开发，启动后延迟3秒把一个平行光隐藏。

- Event：游戏开始？

- Object：场景中的一个点光源。

- Action：Delay和ToggleVisibility。

  <img src="_IMG\Delay-ToggleVisibility.png"  style="zoom:75">

### **4.Working With Blueprint Classes**

Class蓝图可以被场景复用

Class蓝图内自己创建一个点光源：添加一个点光源组件（注意这里不是场景里面点光源的引用了）

<img src="_IMG\AddComponent-PointLight.png"  style="zoom:0">

Class蓝图可以直接拖拽到场景里面

<img src="_IMG\Drag-BluePrint-to-Scene.png"  style="zoom:0">

添加BoxCollider

<img src="_IMG\AddComponent-BoxCollider.png"  style="zoom:0">

通过选中Box对象，来添加一个Overlay Event（之后并没有用到这个Box对象）

<img src="_IMG\AddEvent-OnComponentBeginOverlay.png"  style="zoom:0">

Event，已经关联了Box对象，如果碰撞的对象可以Cast成第三人称控制器，那么执行Toggle Visibility Action。

<img src="_IMG\Character-Collide-to-Change-PointLight-Visibility.png"  style="zoom:50">

### **5.Introduction To Data Types**

添加变量

<img src="_IMG\AddVariables.png"  style="zoom:140">

变量类型

<img src="_IMG\Choose-Variable-Type.png"  style="zoom:120">

拖拽变量，Get / Set

<img src="_IMG\Variable-Get-Set.png"  style="zoom:150">

Action之间的连接（写变量是Action，读变量不是Action）

<img src="_IMG\Action-Connect.png"  style="zoom:0">

### **6.Working With Integers**

删除蓝图连线方法：选中要删除的蓝图连接线，点击ALT+鼠标左键，即可删除。

创建一个Int类型的变量，打印到屏幕和Log中，颜色蓝色，持续2秒。

<img src="_IMG\PrintInt.png"  style="zoom:0">

 整数相加，右键，输入Integer，筛选Action

<img src="_IMG\Print-AddedInt.png"  style="zoom:0">

初始值是2，会同时打印4和10

初始值是2，两次打印都是4，改了值，即使保存。

<img src="_IMG\DelayPrint-AddedInt.png"  style="zoom:0">

### **7.Working With Floats**

### **8.Working With 3D Vectors**

### **9.Working With Booleans**

略

### **10.Branches & Conditioning**

<img src="_IMG\Branch-PrintString.png"  style="zoom:0">

### **11.For Loops**

打印0-15

<img src="_IMG\ForLoop-PrintNum.png"  style="zoom:0">

### **12.While Loops**

从0到9，打印，不断累加Test_While_Num

<img src="_IMG\WhileLoop-PrintNum.png"  style="zoom:0">

### **13.Is Valid Check**

判断对象是否位空

<img src="_IMG\IsValid-CheckObjectIsNull.png"  style="zoom:0">

### **14.Game Mode Blueprints**

**GameMode里面可以存储一些数据（比如：角色拾取的金币数量）**

edit > project settings > Project > Maps & Modes : 默认的GameMode是ThirdPersonGameMode

<img src="_IMG\Edit-ProjectSetting-DefaultGameMode.png"  style="zoom:0">

默认的GameMode位置：Content/ThirdPersonBP/Blueprints/ThirdPersonGameMode

<img src="_IMG\DefaultGameModeInConentBrowser.png"  style="zoom:0">

创建一个Game Mode

<img src="_IMG\CreateGameModeBluePrint.png"  style="zoom:0">

创建一个Int变量，并且把我们的GameMode替换上去

在ThirdPersonCharacter蓝图中，访问MyGameMode蓝图的变量

<img src="_IMG\VisitVariableOfGameMode.png"  style="zoom:0">

### **15.Player Character Blueprints**

创建一个Character。取名MyThirdPersonCharacter。

<img src="_IMG\CreateCharacterBluePrint.png"  style="zoom:0">

给选择角色Mesh，移动角色到胶囊体内部，旋转角色与箭头方向一致，添加动画在角色下面添加相机，在相机项目添加点光源

<img src="_IMG\AdjustMeshWithCollider.png"  style="zoom:0">

<img src="_IMG\SetAnimationForPlayer.png"  style="zoom:0">

把Default Pawn Class替换为新建的CharacterBluePrint

把场景中的角色删了，运行，默认就会启动刚刚创建的角色了。

<img src="_IMG\ChangeDefaultPawnClass.png"  style="zoom:0">

### **思考**

每个蓝图可以自己带对象（Mesh，动画，光源等），本身有一种面向对象的感觉，或者说是一个蓝图就是一个对象集合。

可以利用蓝图来做好对象封装。

### **16.Pawn Blueprints**

UE4快速理解pawn、character、controller三者之间的联系

https://blog.csdn.net/qq_43021038/article/details/124896751?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_title~default-0-124896751-blog-99679087.pc_relevant_multi_platform_whitelistv1&spm=1001.2101.3001.4242.1&utm_relevant_index=3

一 pawn类继承自Actor，在国际象棋中pawn意味着卒、兵，没有生命的一个Actor,在pawn的源码中，相当于一个被控制的角色，这个角色可以是死的，活的，不具有生命特性的，它能够被controller控制，这个controller可以是玩家，也可以是AIcontroller。

二 character类代表角色，继承自pawn，它提供了一个特殊的组件charactermovement,这个组件提供了一个基础的基于胶囊体的角色移动功能，更多的用具有生命属性，移动属性的功能。如果你的功能十分简单不需要移动属性，就不用继承自character。

三 controller类控制器，顾名思义，就是玩家控制角色的一个类，这个类可以是player controller,也可以是AIController,它是控制角色移动，发出命令的核心，有了这个控制器，才能进行绑定输入，转化成对pawn和character的指令。

三者之间，在使用过程中如果需要角色移动属性，就使用character类，如果没有移动属性，就使用pawn,如果说pawn/character是肉体，而controller是操作pawn和character的灵魂。

### **17.Functions, Macros & Events**

他们之间的区别还比较多

https://www.jianshu.com/p/922ac98dd206

函数，就像是Unity的一个SubGraph。

<img src="_IMG\CreateFunction.png"  style="zoom:0">

<img src="_IMG\TestFunction.png"  style="zoom:0">

<img src="_IMG\UseTestFunction.png"  style="zoom:0">

宏，使用起来感觉与函数没啥区别。只是有Inputs和Outputs这两个节点。

宏，可以返回数据？

<img src="_IMG\TestMacro.png"  style="zoom:0">

新建event，在EventGraph中，右键：Add Custom Event

<img src="_IMG\AddCustomEvent.png"  style="zoom:0">

<img src="_IMG\AddCustomEvent2.png"  style="zoom:0">

<img src="_IMG\UseCustomEvent.png"  style="zoom:0">

### **18.Switch on Integer**

就是Switch-Case，参数是一个Int

<img src="_IMG\SwitchInt.png"  style="zoom:0">

### **19.Switch on String**

### **20.Using The Flip Flop Node**

翻转节点

<img src="_IMG\FlipNode.png"  style="zoom:0">

### **21.Working with Gates**

用来开启/关闭一些流程。

### **22.Using Input Events**

第一种方法：右键 > Keyboard Event

第二种方法：Edit > Project Setting > Engine > Input，按键绑定

### **23.Mouse Input Data**

右键 > Input > Event > Mouse Events > Mouse X

鼠标移动，旋转摄像机

### **24. Movement Axis Inputs**

Edit > Project Setting > Engine > Input ：增加两个绑定

<img src="_IMG\AddInputBinding.png"  style="zoom:0">

沿着摄像机的Forward或者Right方向移动

<img src="_IMG\MoveAlongWithCameraDir.png"  style="zoom:0">

### **25.Introduction To Arrays**

通过勾选这里：单一数值，Array，Set，Map

遍历打印数组

<img src="_IMG\VariableArray.png"  style="zoom:0">

### **26.Struct Variable Types**

变量类型

<img src="_IMG\Struct-BreakResult.png"  style="zoom:0">

### **27.Enum (Enumerator) Variable Types**

1，创建一个变量，可以选择预制的枚举

2，在Content Browser里面可以创建一个枚举类型

<img src="_IMG\CreateCustomEnum.png"  style="zoom:0">

### **28.Object & Class Variable Types**

<img src="_IMG\VisibleObjectVariable.png"  style="zoom:0">

### **29.Set Timer by function name**

略