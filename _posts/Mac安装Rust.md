## Mac安装Rust

最近被周围人安利Rust比较有趣，想玩儿一玩儿，去官网看了一下环境的安装方法

![image-20200717203801007](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2020/7/17/1735cd4f0771cd20~tplv-t2oaga2asx-image.image)



一行命令就搞定了

```shell
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```



由于众所周知的原因，网络情况不好的话，可能会一直卡在这个画面20分钟都没什么反应(可以试一下手机热点，一般能成功)

![image-20200717204141592](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2020/7/17/1735cd4f078d131a~tplv-t2oaga2asx-image.image)



然后一种安装方式是用brew来安装，几乎都能成功

```shell
brew install rust
```



然后试了一下HelloWorld，完全没问题，可以很好运行。但是有一个问题，这样安装的话是不带 rustup的



后来找到了一个方式，brew 安装，也带rustup

```shell
brew install rustup-init
// 安装完成后执行
rustup-init
```



大功告成!