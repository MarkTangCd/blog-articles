# Vim Notes

![80C33DEC-ECA0-4EE2-BAE0-F398E6C464E1.webp](https://s2.loli.net/2022/08/26/jOLUBgQZmf1A52k.webp)



>  目前写代码的主力编辑器是NeoVim和SpaceMacs，VsCode也主要是用Vim插件。整理的命令做一下记录，方便查漏补缺

## 基本命令行命令

- ":q!": 退出vim
- ":wq": 存盘退出
- ":s": 执行替换
- ":!": 执行外部命令
- ":edit"(缩写":e"): 编辑文件
- ":w": 写文件
- ":r": 读文件
- ":help": 查看帮助
- 使用Ctrl-D 和 Tab来进行命令行补全



![30347DF5-DC14-42EC-B4D3-E7CEA151F860.png](https://s2.loli.net/2022/08/26/gPyIQMavUTHqVKb.png)

![0CBC1FD3-4AEF-4491-A09E-B899655A27E0.png](https://s2.loli.net/2022/08/26/dZQsL7MD8IFeHb1.png)



### a i w搭配使用演示

![6E365975-F9BA-4EC4-98F6-EEB7E8C53C03.png](https://s2.loli.net/2022/08/26/FNXTedRCOz4bi5U.png)

![E66DFAE7-439D-4A55-8F78-0D98B7C98DFC.png](https://s2.loli.net/2022/08/26/I3JqHLRprKXxYFE.png)



<Ctrl-F> Forward

<Ctrl-B> Backward

半翻页

<Ctrl-U> <Ctrl-D>

<Ctrl-o> 返回到上一个位置

<Ctrl-i> 前进到下一个位置

zz 将当前光标画面移到屏幕中央

数字+G 跳转到指定行

数字+| 跳转到指定列

H(High) 移动到当前屏幕的顶部位置

M(middle) 移动到当前屏幕的中部位置

L(low) 移动到当前屏幕的底部位置

<C-E> <C-Y> 移动屏幕，不移动光标

zt、zz、zb 移动当前行到顶部、中部、底部



![05C5F9D0-2703-4017-BA14-5D9FEDC23A4A.png](https://s2.loli.net/2022/08/26/YfnmZhDACPtc2XI.png)



### VIM删除操作大全

```
:%s/r//g                    删除DOS方式的回车^M 
:%s= *$==                   删除行尾空白 

:%s/^(.*)n1/1$/               删除重复行 

:%s/^.{-}pdf/new.pdf/         只是删除第一个pdf 

:%s/<!--_.{-}-->//           又是删除多行注释（咦？为什么要说「又」呢？） 

:g/s*^$/d                    删除所有空行 ：这个好用有没有人用过还有其他的方法吗？
:g!/^dd/d                     删除不含字符串'dd'的行 
:v/^dd/d                     同上 （译释：v ==&nbspg!，就是不匹配！） 

:g/str1/,/str2/d              删除所有第一个含str1到第一个含str2之间的行 


:v/./.,/./-1join                压缩空行 
:g/^$/,/./-j                  压缩空行 

ndw 或&nbspndW              删除光标处开始及其后的&nbspn-1 个字符。 
d0                          删至行首。 
d$                          删至行尾。 
ndd                         删除当前行及其后&nbspn-1 行。 
x 或&nbspX                  删除一个字符。 
Ctrl+u                      删除输入方式下所输入的文本。 
^R                          恢复u的操作 
J                           把下一行合并到当前行尾 
V                           选择一行 
^V                          按下^V后即可进行矩形的选择了 
aw                          选择单词 
iw                          内部单词(无空格) 
as                          选择句子 
is                          选择句子(无空格) 
ap                          选择段落 
ip                          选择段落(无空格) 
D                           删除到行尾 
x,y                         删除与复制包含高亮区 

dl                          删除当前字符（与x命令功能相同） 
d0                          删除到某一行的开始位置 
d^                          删除到某一行的第一个字符位置（不包括空格或TAB字符） 
dw                          删除到某个单词的结尾位置 
d3w                         删除到第三个单词的结尾位置 
db                          删除到某个单词的开始位置 
dW                          删除到某个以空格作为分隔符的单词的结尾位置 
dB                          删除到某个以空格作为分隔符的单词的开始位置 
d7B                         删除到前面7个以空格作为分隔符的单词的开始位置 
d）                         删除到某个语句的结尾位置 
d4）                        删除到第四个语句的结尾位置 
d（                         删除到某个语句的开始位置 
d）                         删除到某个段落的结尾位置 
d{                          删除到某个段落的开始位置 
d7{                         删除到当前段落起始位置之前的第7个段落位置 
dd                         删除当前行 
d/text                     删除从文本中出现“text”中所指定字样的位置， 一直向前直到下一个该字样所出现的位置（但不包括该字样）之间的内容 
dfc                        删除从文本中出现字符“c”的位置，一直向前直到下一个该字符所出现的位置（包括该字符）之间的内容 
dtc                        删除当前行直到下一个字符“c”所出现位置之间的内容 
D                          删除到某一行的结尾 
d$                         删除到某一行的结尾 
5dd                        删除从当前行所开始的5行内容 
dL                         删除直到屏幕上最后一行的内容 
dH                         删除直到屏幕上第一行的内容 
dG                         删除直到工作缓存区结尾的内容 
d1G                        删除直到工作缓存区开始的内容  
```



### 多文件操作

![13F418FB-98CC-407F-BFED-85A401BD2184](https://tva1.sinaimg.cn/large/e6c9d24egy1h5jznveljnj20ij07u0tf.jpg)

![31F41D6E-8CA5-482C-B3B5-8D9172AFF54B](https://tva1.sinaimg.cn/large/e6c9d24egy1h5jzoe2i72j20jk0eutae.jpg)



### 缓冲区

![1BA24765-CA60-460E-AA5B-9D2C4FF14863](https://tva1.sinaimg.cn/large/e6c9d24egy1h5jzotadf5j20j60a9gmr.jpg)



### 多窗口编辑

![3955D74D-F4C8-4DC8-A905-C98E64D2CC0A](https://tva1.sinaimg.cn/large/e6c9d24egy1h5jzpcgvs6j20jv0lxgo6.jpg)



### 双窗口比较

![788B4619-C3CA-44E5-ABBF-933C6CF07E0C](https://tva1.sinaimg.cn/large/e6c9d24egy1h5jzpztrt8j20ji0hqtay.jpg)



### 多标签页

![952CA83A-5243-477D-9B3B-BB47DC6A9C3A](https://tva1.sinaimg.cn/large/e6c9d24egy1h5jzqkqe8hj20j00bi75f.jpg)

![6A6B0536-C2B1-4226-B221-4AAEF07FCBF9](https://tva1.sinaimg.cn/large/e6c9d24egy1h5jzqua4r0j20j90353yr.jpg)



### NERDTree

![F403123E-0A03-4F39-9593-88CE719D4D60](https://tva1.sinaimg.cn/large/e6c9d24egy1h5jzrdv28tj20k50b8t9y.jpg)



### 正则表达式搜索

![B4BBDF1B-B711-4045-960B-7C8B525FB70E](https://tva1.sinaimg.cn/large/e6c9d24egy1h5jzrurxzrj20jo0h5di4.jpg)

![F90DBE74-28D8-4098-83C0-31D4BD10CD66](https://tva1.sinaimg.cn/large/e6c9d24egy1h5jzs4tua6j20jr0gb0v3.jpg)

![DD1D8DA3-9560-4A51-A8F6-4D2F0867639A](https://tva1.sinaimg.cn/large/e6c9d24egy1h5jzsnndsmj20bt0ekjs6.jpg)



