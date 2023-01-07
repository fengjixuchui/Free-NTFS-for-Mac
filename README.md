# Nigate

一款支持苹果芯片的Free NTFS for Mac小工具软件，[oxfuse](https://osxfuse.github.io)、[ntfs-3g](https://github.com/osxfuse/osxfuse/wiki/NTFS-3G#installation)方案集成整合，与[ezntfs CLI](https://github.com/lezgomatt/ezntfs)异曲同工。

## 实机演示

视频：https://www.bilibili.com/video/BV1XG4y1f79N

![Watch the video](https://fastly.jsdelivr.net/gh/hoochanlon/free-mac-ntfs/shashin/example.png)

## 先决条件

安装homebrew

```shell
/bin/bash -c "$(curl -fsSL https://gitee.com/ineo6/homebrew-install/raw/master/install.sh)"
```

安装python

```shell
brew install python
```

最后调整Mac系统设置：[关闭SIP](https://www.pcbiji.com/212402.html)、[“允许任何来源”](https://jingyan.baidu.com/article/49ad8bce2f5cee1834d8faaa.html)。


## 报错解决

**出现“busy”等错误提示**

![](https://fastly.jsdelivr.net/gh/hoochanlon/free-mac-ntfs/shashin/umount-3g.png)

出现“busy”等无法写入的错误提示，先卸载掉U盘，disk4s1为当前的U盘设备序列名，[官网如是，此类同理](https://github.com/osxfuse/osxfuse/wiki/NTFS-3G)。

```shell
sudo umount /dev/disk4s1
```

```shell
sudo /System/Volumes/Data/opt/homebrew/bin/ntfs-3g /dev/disk4s1 /Volumes/NTFS -olocal -oallow_other -o auto_xattr
```

**文件损坏扔入废纸篓**

![](https://fastly.jsdelivr.net/gh/hoochanlon/free-mac-ntfs/shashin/fileberak.png)

这是苹果签名问题

```shell
sudo xattr -d com.apple.quarantine /Applications/nigate.app
```

## macOS上完全免费的NTFS软件清单

* [easyuefi ntfs](https://www.easyuefi.com/ntfs-for-mac/ntfs-for-mac.html) 
* [paragon ntfs for Mac](https://www.seagate.com/cn/zh/support/software/paragon/#downloads)
* [mounty](https://mounty.app)
* [ntfstool](https://ntfstool.com)

## 感谢

[osxfuse](https://osxfuse.github.io)、[ezntfs](https://github.com/lezgomatt/ezntfs)、[HomebrewCN](https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)、[homebrew-install](https://gitee.com/ineo6/homebrew-install/raw/master/install.sh)提供的支持于帮助。
