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

# 代码示例

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no">
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
    <title>video</title>

    <style>
        .wrap {
            padding-top: 20px;
            text-align: center;
        }
        .wrap video {
            width: 70%;
        }
        .description {
            text-align: center;
            color: #3f3f3f;
            font-size: 14px;
        }
    </style>
</head>
<body>
<div class="wrap">
    <!-- video成像是相反的，可用canvas drawImage 绘制同向图像 -->
    <video id="video" playsinline autoplay controls="true"></video>
</div>
<p class="description" id="description"></p>
</body>

<script>
    var video = document.getElementById('video');
    var description = document.getElementById('description');
    var canvas = document.getElementById('canvas');
    var contraints = {
        audio: false,
        video: {
            facingMode: 'user'
        }
    };
    function successFun (stream) {
        var videoTracks = stream.getVideoTracks();
        video.srcObject = stream;
        description.innerText = 'the video devices is ::' + videoTracks[0].label;
    }
    function errorFun (error) {
        description.innerText = 'meet error::' + error.message;
    }
    navigator.mediaDevices.getUserMedia(contraints).then(successFun).catch(errorFun);

</script>
</html>

```


