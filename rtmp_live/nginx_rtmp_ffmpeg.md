# 开启nginx

```
# 192.168.8.254 机器下
/opt/nginx-1.21.6/sbin
./nginx
```

# 使用 ffmpeg 命令推流

>centos 7
>
>【参考链接】https://blog.csdn.net/grl18840839630/article/details/80694640

推流命令

```
ffmpeg -re -i /opt/nginx-1.21.6/my_videos/messi.mp4 -c copy -f flv rtmp://192.168.8.254:1935/rtmplive/messi
# 注意这是一条命令，不是两条
```

循环推流命令

```
# 视频播放结束会出现一两秒的卡顿后才继续循环播放
ffmpeg -re -stream_loop -1 -i /opt/nginx-1.21.6/my_videos/messi.mp4 -vcodec libx264 -acodec aac -f flv rtmp://192.168.8.254:1935/rtmplive/messi

# 不添加音频
ffmpeg -re -stream_loop -1 -i /opt/nginx-1.21.6/my_videos/messi.mp4 -vcodec libx264 -f flv rtmp://192.168.8.254:1935/rtmplive/messi
```

后台推流

```
# 后台推流，会在该命令执行的目录下生成一个 tuiliu_log.txt
nohup ffmpeg -re -stream_loop -1 -i /opt/nginx-1.21.6/my_videos/messi.mp4 -vcodec libx264 -f flv rtmp://192.168.8.254:1935/rtmplive/messi > tuiliu_log.txt 2>&1 &

# 查看推流的进程
ps -ef | grep ffmpeg

root     24461 19738 59 19:21 pts/0    00:00:16 ffmpeg -re -stream_loop -1 -i /opt/nginx-1.21.6/my_videos/messi.mp4 -vcodec libx264 -f flv rtmp://192.168.8.254:1935/rtmplive/messi

# 杀死推流的进程
kill -9 22461
```

同一个视频推成多路流

```python
import os
import time

tuiliu_num = 2
for i in range(tuiliu_num):
        url_path = 'rtmp://192.168.8.254:1935/rtmplive/messi_' + str(i+1)
        log_name = 'tuiliu_log_' + str(i+1) + '.txt'
        command_t = "nohup ffmpeg -re -stream_loop -1 -i '/opt/nginx-1.21.6/my_videos/messi.mp4' -vcodec libx264 -f flv" + url_path + '>' + log_name + ' 2>&1 &'
        print(command_t)
        time.sleep(1)
        # subprocess.call(['nohup', 'ffmpeg', '-re', '-stream_loop', '-1', '-i', '/opt/nginx-1.21.6/my_videos/messi.mp4', '-vcodec', 'libx264', '-f', 'flv', url_path, '&'])
        os.system(command_t)
        # nohup ffmpeg -re -stream_loop -1 -i /opt/nginx-1.21.6/my_videos/messi.mp4 -vcodec libx264 -f flv rtmp://192.168.8.254:1935/rtmplive/messi_02 > tuiliu_log_02.txt 2>&1 &

        print('num_'+str(i+1)+'_success.')


print('==' * 30)
print("=======>> all_"+ str(tuiliu_num) + "_success.")
print('==' * 30)

```

