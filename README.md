# rstp_live
记录一次通过摄像设备rstp实现实时播放达到直播目的

## 步骤

* [1、下载安装Node.js](#setp1) 
* [2、下载解压ffmpeg](#setp2) 
* [3、下载附件中的rtmp-flv.rar,其中需要修改index中的两处参数（1.relay:ffmpeg需要指向本地的ffmpeg.exe。 2.relay:tasks数组为设备的rstp地址。）](#setp3) 
* [4、使用Nod执行index，命令 ‘Node index’.启动之后使用播放器访问链接(http://ipAddress:port/live/####.flv)已经可以观看了。其中port为index中设置的端口，####为index中tasks的name](#setp2) 
* [5、示例:<br>tasks:{
                app: 'live',
                mode: 'static',
                edge: 'rtsp://admin:passwortd@ipAddress:554/Streaming/Channels/202',
                name: '202',
                rtsp_transport : ['udp', 'tcp', 'udp_multicast', 'http']
            }<br>flv=http://IPAddress:port/live/202.flv ](#setp2) 

* [6、问题记录<br>【谷歌浏览器同时打卡多个flv地址阻塞？解决方案：使用nginx中专一次，配置nginx的http指向node】<br>【为什么不使用ffmpeg直接把rstp转为rtmp？答：rtmp需要使用flash，但是谷歌浏览器正在抛弃flash，将在20年12月份彻底禁用】<br>【流量问题？ffmpeg拉流会一直消耗流量，可以使用程序执行cmd命令来控制启停node,但是这里遇到了坑，使用程序执行cmd时，如果后台运行cmd，使用flv会出现黑屏的情况，所以程序执行cmd启动node时需要将cmd窗口抛出来在桌面显示。】](#setp2) 
