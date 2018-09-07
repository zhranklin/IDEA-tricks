# IntelliJ IDEA 使用技巧汇总
本文为零散的功能点分享, 所以并不会面面俱到, 图中涉及敏感信息较多, 所以有打码, 可能会影响观感, 见谅!

## 最重要的几个快捷键
### 必须知道的快捷键 cmd/ctrl+shift+a
这个叫`[Action...]`, 掌握了这个快捷键, 就等于掌握了所有快捷键。例如重构, 输入refactor this:

![](IDEA.resources/BCEE106A-32C7-44F2-B648-7A26E5B3F0C2.png)

全局搜索:

![](IDEA.resources/87E838CD-901A-4D83-B483-56D038159395.png)

格式化代码:

![](IDEA.resources/E61C15CA-14B5-4EEB-8766-25F465240598.png)

甚至支持fuzzy search:

![](IDEA.resources/8D67C075-150C-4E3F-B146-45B49F271419.png)

所以, 即便你懒到无可救药, 也请你一定要记住这个快捷键

#### 重要提示!!!
由于大家使用的系统不一样, 以及本人对许多快捷键作了修改, 后文涉及到的所有操作都会用类似于`[Find in Path]`这样的格式标出。只要将方括号内的字符串(的一部分)输入到上图中的框内, 就可以完成相关动作。同时, 可以在mac系统上可以直接**看到它的快捷键**。

#### 内置keymap参考
实际上IDEA内置了一份常用快捷键pdf文档, 输入action: `[Keymap Reference]`即可查看。

### (win用户)必须要改的快捷键: Refactor This
这是本人使用频率最高的快捷键之一, 但似乎在windows下的键位非常难按, 建议改一下。重构将在后文重点介绍

## 总览
![](IDEA.resources/724D7C34-ADC9-456D-B619-A11DBFE33985.png)

页面左上方是当前文件的路径, 可以每一个都可以点击进入

右上方则是几个最常用的按钮(可以在设置里面自己定制, 不展开)

![](IDEA.resources/8A0BDA55-98A4-48BA-99C7-1A3A791C16A6.png)

功能则分别是:
- `[Run Anything]`(最新功能, 双击Ctrl呼出, 但因为太新了, 没接入几个java相关的功能, 不好用)
- build
- 选择run configuration, 也就是选择要启动什么东西(tomcat/main方法启动类/springboot工程等等)
- 启动/调试/代码覆盖率测试/profile/concurrency diagram(这两个没用过, 不懂..)/停止
- 更新git(后文详述)/commit/从版本库中查看历史文件/revert代码
- 项目结构(太复杂了, 本文不涉及)
- `[Search Everywhere]`(双击shift呼出)

**重点**: 这几个按钮会在mac的touch bar上出现。

### tool window
左右两边以及底部就是tool window的标签，单击可以打开(废话)。但其实有更优雅的方式: 标签上有个数字, cmd(win下为alt)+数字就可以直接打开或关闭这个窗口

使用完窗口之后, 不需要鼠标单击, 直接按escape键就可以回到编辑窗口。

![](IDEA.resources/01.gif)

![](IDEA.resources/8A0BDA55-98A4-48BA-99C7-1A3A791C16A6.png)

有人说看不到这几个标签按钮, 按两下cmd(win下为alt), 第二下按住, 就能看到了, 建议把这个功能去掉, 截图的这个选项勾上就可以了:

![](IDEA.resources/21A9828B-919D-4D36-BB36-5DD89A5732B5.png)


#### split mode
有一个非常迷但是还蛮好用的功能叫split mode。表面上看tool分为左右下三部分, 但其实每一边都被分成了两部分, 所以其实有六部分。以左边为例:

![](IDEA.resources/208F9E03-4AE4-4764-809B-838B4AF65095.png)

Structure勾选了split mode, 则标签被安排在了左下方, project没勾选split mode, 则在左上方。其唯一的区别是, 在同一边的不能同时显示, 不在同一边的就可以分列显示:

![](IDEA.resources/8DE99D6D-FE63-465E-BEA4-41241E21D1DA.png)

其余同理, 还有floating mode, windowed mode, 字面就看得出来啥意思, 自己实验吧。

接下来就按主题分块介绍

## 代码导航
### Project & Structure
上面的截图再放一遍:

![](IDEA.resources/8DE99D6D-FE63-465E-BEA4-41241E21D1DA.png)

首先最常见的当然是Project窗口, 这里只讲一个, 一个我相见恨晚的按钮:

![](IDEA.resources/39286D7C-44A2-4FE4-9F2E-D392918593C9.png)

![](IDEA.resources/AC7502FA-CD3F-48EF-AAC8-47825D410893.png)

按这个可以迅速定位到当前正在编辑的文件所在位置。

Structure就不详细介绍了, 浏览代码的时候可以查看所有成员变量/方法等, 以及可以快速定位。上面的按钮选项也很有用, 可以自己试一下。

### `[Search Everything]`(双击shift)
![](IDEA.resources/236C1D07-6075-40BF-BB0F-CECF56A34250.png)

包括了文件/类/符号(field/method), 甚至Action..

不过稍微大一点的项目就不是很实用了, 因为搜索结果太多了

个人最常用的也就个search:

- 文件: cmd+shift+o`[File...]`
- 类: cmd+o`[Class...]`

### `[Find...]` & `[Find in Path...]`
快捷键分别是cmd+f/cmd+shift+f, 有这几个选项:

![](IDEA.resources/87FD8297-AD04-4E23-A6C4-C666DF5FF244.png)

`[Replace...]` & `[Replace in Path...]`与前者快捷键很相似, cmd+r/cmd+shift+r

实践过程中发现正则表达式的一个高级特性非常重要: 零宽断言(不展开)

例如我们打算把掉user1/user2/user3替换成client1/client2/client3, 就可以这么做(没看懂就好好复习一下正则吧):

![](IDEA.resources/CA5231D8-B455-4B9C-A06C-3DF95256A534.png)

IDEA也开始支持了sublime一类编辑器提供的功能: 批量选中编辑

![](IDEA.resources/%E6%89%B9%E9%87%8F%E9%80%89%E4%B8%AD%E7%BC%96%E8%BE%91.gif)

不过好像前端的同学更习惯于这种模式。

搜索的filter选项比较实用, 可以选定搜索上下文, 是代码, 字符串还是注释:

![](IDEA.resources/D73CF133-F630-495A-BF5A-F1EB60D00F01.png)

可以全部替换, 也可以一个个换, 也可以排除掉几个再全部替换

![](IDEA.resources/02.gif)

`[Replace in Path]`也差不多, 注意多了一个file mask选项, 以及四个选择范围的选项卡(自己研究去吧):

![](IDEA.resources/C6105306-C1BA-4A5D-A563-20B3532341DB.png)

![](IDEA.resources/40F91FD5-C1EC-4D2C-943C-2C12FE340457.png)

如果打算慢慢替换, 可以点击Open in Find Window, delete键排除:


![](IDEA.resources/03.gif)

结果如下

![](IDEA.resources/8019A2C1-F306-4DCF-91E5-1C174804174B.png)

### bookmark及favorate
记得左下角的favorate标签吗?打开来长这样

![](IDEA.resources/2B8100AC-52A3-41AC-86B3-F96163A5CD1E.png)

favorate有点鸡肋, 跳过不讲, 这里重点讲讲bookmark

#### bookmark: 快速标记/跳转
![](IDEA.resources/2BF7B727-EF29-4ECE-9F1A-C6E69D276BAF.png)

#### `[Show Bookmarks]`, `[Toggle Bookmark]`以及Bookmark注解
`[Show Bookmarks]`, `[Toggle Bookmark]`我自定义了快捷键, 分别是ctrl+b和ctrl+鼠标单击

显示所有书签之后, 就能看到所有书签以及其对应的代码位置, 还可以进行标记, 可以说很贴心了。

整一个流程就是这样的:

![](IDEA.resources/04.gif)

### 基本代码导航操作
- `[Back]`cmd+'['/`[Foward]`cmd+']' 代码前进/后退
- `[Select Previous Tab]`cmd+shift+'['/`[Select Next Tab]`cmd+shift+']' 上一个/下一个tab
- 代码左侧子类父类导航
  ![](IDEA.resources/F3387958-3ECA-4A86-AEC0-9917E14A9514.png)
  ![](IDEA.resources/90562CF5-1070-4BB3-9C98-8B0C7F313B29.png)
  ![](IDEA.resources/E696212B-02E4-463A-9CB3-075B9CA0BF6D.png)
  ![](IDEA.resources/A40413E4-C384-4516-A85B-7C2A0F3AE49E.png)

## coding
### 基本操作
实际上IDEA的基本操作就已经十分方便了:

![](IDEA.resources/1F7D1EF5-04CF-4542-BEE8-777B2338A36A.png)

![](IDEA.resources/1AAC18B3-433C-49F0-B1B4-E3F66975BBE6.png)

![](IDEA.resources/code%20basic%20edit.gif)

`[Generate]`cmd+n 看图自然懂得

![](IDEA.resources/B4B7ACF5-7E46-417A-9BA5-43DFEA956BFE.png)


### 补全
代码补全分为`[Base Completion]`(ctrl+space)和`[Smart Completion]`(ctrl+shift+space)

**重点**: 只要填写驼峰首字母就可以了, 不用写全, 比如toString直接打ts即可

smart completion的特点是基于类型的补全, 在填写枚举的时候比较实用

![](IDEA.resources/completion.gif)


**重要** 最好取消勾选 match case:

![](IDEA.resources/1D6252BB-8306-4FF3-B15B-932E42190E73.png)

自动补全以及显示参数(cmd+p)

![](IDEA.resources/05.gif)

### postfix completion
这可能是普通人想也想不出来的需求, 比较强大, 动图里展示最常用的几个操作:
- .var (提取变量)
- .for
- .if
- .par (括号包围)

![](IDEA.resources/06.gif)

![](IDEA.resources/dotfor%20dotif.gif)

还有一个.field提取成员变量, 频率稍低。其实还有很多, 自己去实验吧

### option+enter
这是体现intelliJ"智能"的一个功能: intention, 往往与inspection配合出现, 后者为一些代码优化点的标识, 如标黄、波浪线等, 而前者则为对用户意图的猜测, 不仅限于优化点, 也包括一些用户可能需要的操作, 包括重构、language inject等。

![](IDEA.resources/08.gif)

这个比较多 就不详述了, 总之在编码与重构的时候刻意使用intention能够节约一些时间, 例如:

![](IDEA.resources/C11E1680-A83D-4958-BDB7-C79348D6ABAD.png)

### live template
看图。

![](IDEA.resources/live%20template.gif)

foreach, 不过和postfix completion一比就相形见绌了

![](IDEA.resources/foreach%20template.gif)

## language inject
在用字符串编写一些代码的时候(例如SQL), 容易出现拼写错误、语法错误等问题。在字符串处触发intention即可, 效果如下:

![](IDEA.resources/A1A2EFFF-765D-490C-B06F-90072EB4DE65.png)

提供的补全还算流畅:

![](IDEA.resources/inject.gif)

如果事先在`[Database]`中加入了相关的数据库配置, IDEA还会根据数据库的schema进行错误提示:

![](IDEA.resources/BAD7494A-6C63-4D32-8F07-E2B47A3AFE7C.png)

ReGex:

![](IDEA.resources/FC69EE4D-2CDD-42B2-B63E-F0644697DEC7.png)

发现一个intention:

![](IDEA.resources/1511297A-5B64-4140-9BA6-CEE92790F301.png)

![](IDEA.resources/775F1BE4-0E14-4CA9-8001-A666188263EE.png)

java:
使用前

![](IDEA.resources/9C7AB17C-5007-45A2-96C5-13754914D6F7.png)

使用后(不过也仅限于词法分析级别的注入)

![](IDEA.resources/7D0C6F6F-1DA7-4A53-AE28-368CCE974E8D.png)

## 重构
### `[Refactor This]`
重构的操作非常多, 快捷键也很多。但只用记一个`[Refactor This]`就够了:
![](IDEA.resources/AFB53662-F2AF-4111-A10B-5CD1EA60BB45.png)

rename就不解释了, change signature:

![](IDEA.resources/change%20signature.gif)

### Extract
提取操作除了前面提到的提取参数外, 还可以提取至local变量/常量/成员字段。

此外, 除了与变量相关的提取, 还有提取到接口/父类以及提取到方法等常用重构。这里结合日常需求展示一下method:

![](IDEA.resources/method.gif)

### inline
字面意思:

![](IDEA.resources/inline.gif)

### intention
有意触发intention可以实现一些重构的目的, 这里仅举两例:

#### extract
前面添加参数事实上意味着要使用这个参数, 那么就可以有意的触发intention:

![](IDEA.resources/parameter%20insp.gif)

上图同时覆盖了提取变量/成员字段的重构。

#### 接口添加方法与实现
避免写接口与实现时重复编写签名, 以及避免编写返回类型(尤其在返回类型很复杂时适用):

![](IDEA.resources/interface.gif)

其实类似的操作有很多, 原理都是利用IDEA会通过以来分析推测用户的可能产生的意图, 达到辅助的目的。

## VCS
### vcs面板
![](IDEA.resources/F0E95E73-CFC5-47EE-9F36-5F6BE1FF2549.png)
基本上看一下就能知道是干啥的, 框选的按钮比较实用, 选中之后, 在合并分支的提交之后, 优先显示合并分支的提交

选中前

![](IDEA.resources/AB1CC83E-7B35-4B1B-8300-70940FD0E398.png)

选中后

![](IDEA.resources/D925C6DA-8243-464A-80E9-CBAF7370AA02.png)

可以迅速看出分支合并的情况

### 操作
和重构一样, 版本管理部分可以只记忆一个快捷键`[VCS Operations Popup]`(好像默认是没快捷键的):

![](IDEA.resources/BB886FA1-EF04-43FB-9ADD-32800BD8C356.png)

打开后长这样:

![](IDEA.resources/C819A41F-D7B3-4D11-9C89-BA3293323593.png)

不过IDE窗口右上角的Update按钮, 在这里没有..

### commit/push
不用讲了, 和git命令的逻辑一样

### update
实际上update经历了一下过程:

- stash, 将未提交的修改暂存, 保证本地仓库clean
- fetch, 拉取远程所有分支
- 如果当前分支绑定的远程分支有新提交, 则merge(有冲突则弹出merge窗口手动操作)
- unstash, 有冲突则弹出merge窗口

尽量避免在公共分支上修改代码, 则可以避免不必要的merge操作

如果不想合并当前分支绑定的远程分支, 但又想要合并其他分支, 则不能update, 而是fetch, 然后将其他分支合入。

### 场景: 紧急fix
如遇到紧急bug, 但是如果此时手头在其他分支, 而且有大量未提交代码, 就需要暂存当前工作:
- stash
  ![](IDEA.resources/086BC834-6C8D-4513-AFDD-5428A1A51D73.png)
  ![](IDEA.resources/79A3B532-21F4-457B-A18D-CA654E6D955A.png)
- checkout公共分支
  ![](IDEA.resources/25F995F9-6FA1-4988-8BDC-F2D12F8B1CA9.png)
  ![](IDEA.resources/55137B31-9117-4E47-97E8-AB8C4F9911B7.png)
- udpate
  ![](IDEA.resources/0D758309-E862-4193-B372-C70E11FC8E2F.png)
  

如果bug是改一行配置就能解决的, 或者确定不会产生影响, 可以不用新建分支, 否则需要新建一个fix分支, 修复bug后将fix分支合入(如有)

接下来就是还原之前的工作:
- checkout之前的分支
- unstash
  ![](IDEA.resources/792B0209-6005-4EF9-BBC5-2B9689500937.png)

可勾选pop stash, 成功unstash之后这个stash会被删除

### 代码跟踪
- show history不用详细说了吧
- annotate: 行号处右键
  ![](IDEA.resources/BA14987E-8800-49E2-B57D-BA73A3001C39.png)
  ![](IDEA.resources/BCC4DE78-E4AA-471A-940C-0B93E7905865.png)
- 脏(未提交)代码
  - 修改
    ![](IDEA.resources/033CE6AB-453D-43EE-9473-CA98768D23B2.png)
  - 删除
    ![](IDEA.resources/F23A412C-F72B-43A1-B88D-C32E001C35CC.png)
  - 新增
    ![](IDEA.resources/86565C8A-CC9A-4183-A030-68B8DD23975F.png)
  - 单击查看diff及还原代码
    ![](IDEA.resources/7704491D-2E7D-4C5E-B268-ACD3C81F5A60.png)

## debug
### 断点
断点可以右键:

![](IDEA.resources/28594E2D-96FE-426A-88A4-5E4C591DF0ED.png)

点击more统一管理以及详细配置(基本上覆盖了所有需求):

![](IDEA.resources/462BC683-0270-4289-8FCE-7558E97C8340.png)

### 调试窗口
![](IDEA.resources/80751A3D-325E-448B-9B1A-8DEB29AEBC31.png)
图中所示的其实是spring boot的run dashboard, 左侧竖排按钮分别是:
- |
  - run模式重启 
  - debug模式重启 
  - 停止 
- | 
  - update(热部署) 
- | 
  - 继续 
  - 暂停
  - 显示所有断点(和前面的窗口一样)
  - mute(暂时关闭断点监听) 

![](IDEA.resources/2C27DD09-FA08-467E-B82E-50537C92A5D2.png)


右上角几个按钮:

￼![](IDEA.resources/3671F519-30D4-4E91-8D51-13165682F119.png)

中间几个就不介绍了
左1: 跳转回当前断点所在位置
右2计算器: 在断点所在上下文计算表达式
最右: Stream API调试, 后面讲

![](IDEA.resources/B0438406-0D6E-40EF-A063-8B699EB9AFC6.png)

最右边两个按钮, 分别可以查看断点命中统计, 以及堆空间内的对象

中间的栈帧、线程、变量就不多说了

### 远程调试
说出来你可能不信, 远程调试非常简单

第一步, run configuration里新建Remote

![](IDEA.resources/600EA57C-F006-4B5F-A15D-CE1B2920D3B3.png)

第二步, 填写相关参数: ip、port、启动类, 把生成的启动项复制下来

![](IDEA.resources/327290E7-786B-41B0-84EB-C623DC537462.png)

第三步, 将复制的启动项加入到远程jvm

第四步, 启动调试

**注意** 这个操作有一定危险性, 一定不要把这个启动项传播到线上!!

### 热部署
热部署是一个重要功能, 可以避免重启, 合理使用的话, 可以显著减小debug时间, 适合以下场景(仅为举例):
- 拼写错误
- sql语句调试
- restTemplate调试(结合表达式计算不断尝试)
  - 请求参数修正
  - 响应解析失败先查看body(Dto.class换成String.class)

#### tomcat
以前用过tomcat的热部署, 需要稍微配置下, 贴个文档, 不详细介绍了:
<https://blog.csdn.net/wei19880402/article/details/75529231>

#### springboot
springboot其实原生支持热部署, 在idea的run configuration里稍微修改下就能启用

![](IDEA.resources/E6AD5016-3341-4719-80D0-FAA09F7D5866.png)

这样单击update按钮(不是git那个)就能更新类文件

也可以使用on frame deactivation, 文件修改的时候就触发, 但是个人不推荐, 因为太过频繁更新可能导致不稳定, 而且在修改过大的时候(例如添加新方法)会导致交换类文件失败, 不注意的话很容易搞不清到底会执行啥代码

![](IDEA.resources/hot%20swap.gif)

#### JRebel
收费, 没用过, 买不起

#### 注意
- 对注解等无效
- 无法添加新方法, 修改方法签名
- 不要过分信任这个功能, 过于复杂的修改后后update, 可能会导致无法预期的行为

### Stream API调试
新版本更新了一个惊为天人的功能

![](IDEA.resources/ACCD270C-9BD3-4D59-BACE-A29D6429AEFE.png)

![](IDEA.resources/A2896CDC-3571-438B-B944-203C828D80E1.png)

![](IDEA.resources/1B6BE6B8-68F9-4F9C-8A4A-C3DD369E15E9.png)

## Database
敏感信息太多, 自己研究下吧= =
