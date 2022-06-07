# webRTC-from-chat


### 注意视频邀请方和被邀请方
A方：发送视频邀请
行动关键点：
  【1、获取本地摄像头流】
  【2、推视频流到 RTCPeerConnection】 
B方：
需要注意A方发送邀请后，B方需要接受邀请 ：侦听消息：video-offer，执行函数handleVideoOfferMsg()
【处理 本地接受到视频电话请求offer；创建自己的RTCPeerConnection，并推送到本地媒流，最后回复呼叫着】
  行动：
  创建视频会话的 RTCPeerConnection，启动ICE服务
  接受视频流，开启本地流，启动推流
    设置处理邀请方的远程描述，设置本地描述并发送视频接受应答
A方：
  处理视频接受应答video-answer: handleVideoAnswerMsg()
    设置对方的发送的描述为远程描述。


    todo:再详细一下，结合图示；
## 问题
1、Uncaught TypeError: Cannot read properties of undefined (reading 'getUserMedia')

  回答1：html5调用摄像头拍照如果在localhost下没有问题，而部署服务后碰到如下的错误：
Uncaught TypeError: Cannot read properties of undefined (reading 'getUserMedia')
这是因为webrtc需要使用https
作者：allenjcheng
链接：https://www.jianshu.com/p/53368a2ea9a1
  回答2：而使用 http://localhost/xxxx/xxxx来调用摄像头则没有任何问题，这是因为浏览器有安全设置。
进行如下设置，则可以放开录制权限：
chrome://flags/#unsafely-treat-insecure-origin-as-secure
在输入框中输入远程服务地址，将右侧的按钮，调整为enabled，然后点击右下角的重启按钮。
再次使用ip地址来访问服务，调用摄像头，就一切正常。 
https://blog.csdn.net/yunzhonghefei/article/details/120290541
 
