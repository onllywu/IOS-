# IOS-浏览器调用摄像头的方法
navigator.mediaDevices.getUserMedia()

在IOS下的浏览器调用摄像头需要注意一下几点
```
1、仅限IOS11以上系统
2、仅限safari浏览器
3、调用方法为navigator.mediaDevices.getUserMedia()
4、video必须带有playsinline autoplay controls="true"三个属性
5、video不能为display:none（可用透明度、z-index解决显示问题）
6、网页必须为https或者localhost

```


