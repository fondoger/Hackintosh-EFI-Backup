# Hackintosh-EFI-Backup
for K650D-i5-D3.


## 黑苹果配置教程

声卡：
http://bbs.pcbeta.com/forum.php?mod=viewthread&tid=1754054


** 屏蔽独显并开启水波纹的办法 **

// 单独使用K650D i7 D2 EFI 文件无法屏蔽独显，但能开启水波纹
// 单独使用k650d-i5-d3-clover 文件无法开启水波纹
正确的办法：
1. 先使用K650D i7 D2 EFI文件进入MAC
2. 再使用k650d-i5-d3-clover中的ACPI, config.plist, kexts 替换掉之前的文件。
// 可能只需要替换config.plist
PS: 使用该办法会导致菜单栏花屏：
解决办法：http://bbs.pcbeta.com/viewthread-1564954-1-1.html
替换的文件(可根据上面两个config.plist找出该放在那儿，此外，这部分还有好多不相同的补丁）
```
	<dict>
		<key>Comment</key>
		<string>Enable 9MB cursor bytes, 0x0a260006</string>
		<key>Disabled</key>
		<false/>
		<key>Find</key>
		<data>
		BgAmCgEDAwMAAAACAAAwAQAAYAA=
		</data>
		<key>Name</key>
		<string>AppleIntelFramebufferAzul</string>
		<key>Replace</key>
		<data>
		BgAmCgEDAwMAAAACAAAwAQAAkAA=
		</data>
	</dict>
```
PS: 该方法可以正常调节亮度, shift+F2/F3调节亮度ß
成功的DSDT补丁（评论最下方）：
http://bbs.pcbeta.com/forum.php?mod=viewthread&tid=1678681&page=1

** 其他可能有用的文件 **


** 万能声卡驱动 **
将 VoodooHDA.kext 放入System\Library\Extension, 然后使用kext修复权限。
PS: 最好删除AppleHDA.kext
PS: 已知的问题，开机爆音，不过平时使用没有杂音。

** 无线网卡配置教程（针对AR9485） **
参考帖子： https://www.reddit.com/r/hackintosh/comments/7hljk1/is_there_any_way_to_get_my_atheros_ar9485_to_work/

## 参考帖子

* [主要教程](http://bbs.pcbeta.com/viewthread-1659550-1-1.html)
* K650D i7 D2 EFI 文件提供: [K650d i5/i7 d2 10.13.3 几乎完美配置分享](http://bbs.pcbeta.com/forum.php?mod=viewthread&tid=1776532)
* k650d-i5-d3-clover 文件提供: [来自github](https://github.com/daggeryu/k650d-i5-d3-clover)

## 可能有用的帖子

* [神舟K650D i7 D3 基本上算完美吧，分享EFI](可能是shift+F2/F3调节亮度的来源)
* 一份DSDT文件， 能够屏蔽独显，但没有开启水波纹[参见帖子最下方评论](http://bbs.pcbeta.com/forum.php?mod=viewthread&tid=1678681)