# PhpStorm

* 如何设置断点
* 酷炫操作
* 快捷键


--------------------------------


### 如何设置断点
```text
参考链接： (建议先看图文，看一遍知道怎么回事了，下次忘记了就可以看精简版的文字笔记了)
https://www.php.cn/php-weizijiaocheng-387522.html
http://blog.sina.com.cn/s/blog_65cee6990102vlb4.html
其他信息参考:
https://xdebug.org/docs/profiler
```

```text
纯文字版本：
准备：chrome已经安装xdebug插件； php已经安装xdebug扩展并开启。
修改php.ini文件，注意：修改对应版本的php.ini文件, 注意wamp是有两个php.ini文件的，一个公共的，一个是对应版本php的。加载的是哪个就修改哪个，如果无法确认，就同时修改

[xdebug]  
zend_extension = "e:/wamp64/bin/php/php7.1.16/zend_ext/php_xdebug-2.6.0-7.1-vc14-x86_64.dll"
xdebug.remote_enable = On  
xdebug.remote_handler = dbgp     
xdebug.remote_host= localhost  
xdebug.remote_port = 9000  
xdebug.idekey = PHPSTORM
    
打开phpStorm，进入File > Settings > Languages&Frameworks > PHP，这里要interpreter浏览，填D:\xampp\php\php.exe，自动识别版本。
进入File > Settings > PHP > Servers，这里要填写服务器端的相关信息，name填localhost，host填localhost，port填80，debugger选XDebug。
进入File > Settings > PHP > Debug，看到XDebug选项卡，port填9000，其他默认。
进入File > Settings > PHP > Debug > DBGp Proxy，IDE key 填 PHPSTORM，host 填localhost，port 填9000，点OK退出设置。
Run > Edit Config > 如果是需要登录的页面则选择web Application)
```


### 酷炫操作
查找一个函数在哪里被调用, 或查看被调用的函数在哪里被定义:Ctrl + 鼠标左键(Ctrl + B);

快速插入一个文件,或者一个构造函数 Alt + Insert(或者空白处右键->Generate); 

快速新建方法: 例如$this->doStuff($action); doStuff不存在时候, 光标移动到字符中按Alt + Enter
(参考: https://stackoverflow.com/questions/23090063/phpstorm-create-a-method-from-its-call)

如何自动换行: Settings-editor-general-use soft wraps in editor

更新(生成)注释:光标移动到参数中, Alt+Enter两次, 结果: 
```php
    public static function findRecentComments($limit = 10){}

    /**
     * @param int $limit
     * @return array
     */
    public static function findRecentComments($limit = 10){}
```

PHPSTORM如何配置模板文件,settings -> Editor -> File and Code Templates -> Files或者Includes中,
```HTML
    <!-- 修改html头文件：-->
    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "
    http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
    <html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <meta charset="UTF-8">
        <title>#[[$Title$]]#</title>
    </head>
    <body>
    #[[$END$]]#
    </body>
    </html>
```     
```PHP
    //php 头文件: 
    /**
     * TestGuest Version1.0
     * @date: ${DATE}
     * @author:
     * @param:
     */

```


### 快捷键
 
    https://segmentfault.com/a/1190000004225643:
    ctrl+shift+up/down (移动行、合并选中行，代码选中区域向上/下移动) 
    alt+shift+向上/下 箭头  移动当前行                                
    shift 双击-- search everywhere ;

    CTRL+N 查找类
    CTRL+SHIFT+N 全局搜索文件 ,优先文件名匹配的文件, 如果文件名后面放置斜杠'/',表示搜索一个文件夹( http://stackoverflow.com/questions/27941412/is-there-a-way-to-search-for-folder-directory-in-phpstorm )
    CTRL+SHIFT+ALT+N 查找php类名/变量名 ,js方法名/变量名, css 选择器
    (参考链接: https://www.jetbrains.com/help/phpstorm/2016.3/navigating-to-class-file-or-symbol-by-name.html )
    

    点击左侧小圆圈--查找当前文件在文件夹中的位置

    CIRL+B 找变量的来源，跳到变量申明处 (CTRL+ 鼠标单击 也可以)
    CTRL+ALT+B 找到继承该接口或者父级 的所有子类, 统计所有子类个数
    CTRL+SHIFT+B 找变量的类 (不太懂欢迎评价)
    CTRL+G 定位行，跳转行
    CTRL+F 在当前窗口查找文本
    CTRL+SHIFT+F 在指定路径查找文本字符
    CTRL+R 当前窗口替换文本
    CTRL+SHIFT+R 在指定路径替换文本
    CTRL+E 最近打开的文件
 
    自动代码
    CTRL+J 自动代码提示，自动补全
    也可以直接输入对应的简拼，按下tab键即可（类似linux命令补全）
    ALT+回车 导入包,自动修正
    CTRL+ALT+L 格式化代码
        ------可以使得等号对齐
        @ 使用前需要配置
        // 等号对齐
        Editor->Code Style->Wrapping and Braces->Align consecutive assignments
        // 数组元素对齐
        Editor->Code Style-Other->Align key-value pairs
 
    参考链接: http://www.oschina.net/news/62651/phpstorm-9-eap-141-1224?p=1
    CTRL+ALT+I 自动缩进
    CTRL+ALT+SPACE 类名或接口名提示（与系统冲突） 提示类名关键字 (abstract public ...)
    CTRL+P 方法参数提示，显示默认参数
    ALT+INSERT 生成代码(如GET,SET方法,构造函数等) , 光标在类中才生效
    CTRL+ALT+O 优化导入的类和包 需要配置
    CTRL+SHIFT+SPACE 切换窗口
    CTRL+SPACE空格 代码自动完成，代码提示,一般与输入法冲突
    CTRL+ALT+T 把选中的代码放在TRY{} IF{} ELSE{} 里
 
    复制快捷方式
    F5 复制文件/文件夹
    CTRL+C 复制
    CTRL+V 粘贴
    CTRL+X 剪切,删除行
    Ctrl + Y 删除行插入符号
    CTRL+D 复制行 , 快速分布li标签等
    CTRL+SHIFT+V 可以复制多个文本,将前几次复制的文本保存下来了
 
    高亮
    SHIFT+F2 高亮错误或警告快速定位错误，多个错误循环高亮
 
 
    本地历史VCS/SVN
    Ctrl + K 提交项目VCS
    Ctrl + T 更新项目从VCS
    Alt + Shift + C 查看项目最近文件版本变化文件 , CTRL+E 只是查看修改过的文件
 
    Alt + ` (table 上面的点) 快速弹出VCS菜单
 
    其他快捷方式
    CTRL+Z 倒退(代码后悔)
    CTRL+SHIFT+Z 向前  (反撤销!!!)
    CTRL+H 显示类层级关系图，继承/实现关系
    Ctrl +F12 文件结构弹出 类似 ALT + 7
    CTRL+W 块状选中代码，连续按会有其他效果 Ctrl+Shift+W 减少当前选择到以前的状态
    CTRL+O 魔术方法, 在php类体中有效
    ctrl+shift+i 快速查看变量或方法定义源 , 也可以鼠标按住+CTRL
    CTRL+ALT+F12 资源管理器打开文件夹，跳转至当前文件在磁盘上的位置
    CTRL+ [] 光标移动到{}[]开头或结尾位置
    CTRL+SHIFT+[] 直接选中块代码 = CTRL+W 按好几下
    SHIFT+ALT+INSERT 竖编辑模式
    CTRL+/ 单行注释/取消注释
    CTRL+SHIFT+/ 块状注释/取消块状注释
    Ctrl+Shift+U 选中的字符大小写转换
    ctrl + '-/+':可以折叠项目中的任何代码块,包括htm中的任意nodetype=3的元素，function,或对象直接量等等。它不是选中折叠，而是自动识别折叠。
    ctrl + '.': 折叠选中的代码的代码
    CTRL+ALT←/→ 返回上次编辑的位置
    ALT+←/→ 切换代码视图，标签切换
    ALT+↑/↓ 在方法间快速移动定位
    ctrl+shift+enter(智能完善代码 如if())
    ctrl+shift+up/down (移动行、合并选中行，代码选中区域向上/下移动) *****
    alt+shift+向上/下 箭头  移动当前行                                 *****
    SHIFT+F6 重命名,重构当前区域内变量重命名/重构 不但可以重命名文件名，而且可以命名函数名，函数名可以搜索引用的文件，还可以重命名局部变量。还可以重命名标签名。
    alt + '7':显示当前的类/函数结构。类似于eclipse中的outline的效果。试验了一下，要比aptana的给力一些，但还是不能完全显示prototype下面的方法名。
    Alt + Shift + I 检查当前文件与当前的配置文件
 
    编辑
    Ctrl + Q 快速文档查询
    ALT + INSERT 生成的代码...器（getter，setter方法，构造函数）
    Ctrl + O 覆盖方法
    Ctrl + I 实现方法
    Ctrl + J 活动代码提示
    Alt + Enter 显示意图的行动和快速修复
    Shift + Tab 键缩进/取消缩进选中的行
    Ctrl + Shift + J 智能线连接（仅适用于HTML和JavaScript）
    Ctrl + Enter 智能线分割（HTML和JavaScript）
    Shift + Enter 开始新的生产线
    Ctrl + Delete 删除字（word）
    Ctrl + Backspace 删除整个字 ,单纯Backspace单个字符删除
 
    运行
    Alt + Shift + F10 选择的配置和运行
    Ctrl + Shift + X 运行命令行
    Alt + Shift + F9 选择配置和调试
    Shift + F10 运行
    Shift + F9 调试
    Ctrl + Shift + F10 运行范围内配置编辑器
    Ctrl+Shift+H 方法的层次结构
    Ctrl+Alt+H 呼叫层次
    CTRL+Q 显示代码注释
    ALT+F1 选择当前文件或菜单中的任何视图工具栏
    CTRL+UP/DOWN 光标跳转到编辑器显示区第一行或最后一行下
    ESC 光标返回编辑框
    SHIFT+ESC 光标返回编辑框,关闭无用的窗口 !!!!!
    CTRL+F4 关闭当前的编辑器或选项卡
    Ctrl + Alt + V引入变量
    Ctrl + Alt + F 类似引入变量
    Ctrl + Alt + C引入常量
    Ctrl + Tab 键切换选项卡和工具窗口
    Ctrl + Shift + A 查找快捷键
    Alt + ＃[0-9] 打开相应的工具窗口
    Ctrl + Shift + F12 切换最大化编辑器
    Alt + Shift + F 添加到收藏夹
    Ctrl +反引号（`） 快速切换目前的配色/代码方案/快捷键方案/界面方案
    Ctrl + Alt + S 打开设置对话框（与QQ冲突）
 
    调试
    F8步过
    F7步入
    Shift + F7智能进入
    Shift + F8步骤
    ALT + F9运行到光标
    Alt + F8计算表达式
    F9恢复程序
    Ctrl + F8切换断点
    Ctrl + Shift + F8查看断点
 
    导航
    Shift + Esc键隐藏活动或最后一个激活的窗口
    Ctrl + Shift + F4关闭活动运行/消息/ /...选项卡
    Ctrl + Shift + Backspace键导航到最后编辑的位置
    Ctrl + Alt+B 到实施（S）
    Ctrl + Shift+I 打开快速定义查询
    Ctrl + U 转到super-method/super-class
    Alt + Home 组合显示导航栏
 
    书签
    Ctrl + F11切换书签助记符
    Ctrl +＃[0-9]转到编号书签
    Shift + F11显示书签
 
    Esc键编辑器（从工具窗口）
 
    F1 帮助千万别按,很卡!
    F2（Shift+F2） 下/上高亮错误或警告快速定位
    F3 向下查找关键字出现位置
    F4 查找变量来源
    F5 复制文件/文件夹
    F6 移动
    F11 切换书签
    F12 返回到以前的工具窗口
    修改文件作者
    设置搜索 File and Code Templates
 
 
