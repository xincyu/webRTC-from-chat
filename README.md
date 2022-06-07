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
 
