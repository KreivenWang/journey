下载好最新的3.2，直接解压缩到C:\Users\你的用户名\AppData\Roaming\[![](https://i0.hdslb.com/bfs/reply/9f3ad0659e84c96a711b88dd33f4bc2e945045e0.png)SideQuest](https://search.bilibili.com/all?from_source=webcommentline_search&keyword=SideQuest&seid=2818238117030016858&from_avid=814646920&from_comid=259884408321)，（我就是弄了一晚放错地方了，不是放在安装sidequest的安装目录，是要放在C盘上面的地址，）把scrcpy-win64-v3.2文件夹名改为scrcpy-win64-v2.0就可以了


```
scrcpy --video-source=display --audio-source=output --record=myfile.mp4 --shortcut-mod=lctrl --crop=1224:768:0:0 --max-size=1920 --angle=23 --video-codec=h265
```

```
scrcpy --video-source=display --audio-source=output --record=myfile.mp4 --shortcut-mod=lctrl --video-codec=h265 --display-id=10
```
```
scrcpy --list-displays
```


> Or Steam Link does just fine😏