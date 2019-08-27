# Idea 

* 配置idea编辑器开发php,python
* 重启编辑器,解决莫名其妙的问题
* 添加代码片段,提高开发效率

--------------------------------

### 配置idea编辑器开发php,python

> File -> Plugins -> Marketplace 搜索相应语言插件,然后点击Install，重启编辑器

### 重启编辑器
> File -> Invalidate Caches / Restart -> Invalidate and Restart(清除缓存并重启)

### 添加代码片段
```text
File -> Settings -> Editor -> LiveTemplates

点击右侧+, 选择template group, 输入自定义名称, 任意输入, 确定

选择刚才新建的分组,再次点击+, 选择live template,abbreviation替换为缩写字符, 比如stri,

templates text替换为你真正想输入的字符, 比如String

点击define, 勾选你想生效的语言环境

打开代码区输入吧, 比如stri, 按tab(默认,同样可以自定义)键, 会自动生成String
OK.大功告成

```
