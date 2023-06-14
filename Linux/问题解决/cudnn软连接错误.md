```
(base) root@rtx2060:/home/simple/Desktop# sudo ldconfig
/sbin/ldconfig.real: /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn_adv_infer.so.8 is not a symbolic link

/sbin/ldconfig.real: /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn_ops_infer.so.8 is not a symbolic link

/sbin/ldconfig.real: /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn_cnn_infer.so.8 is not a symbolic link

/sbin/ldconfig.real: /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn_adv_train.so.8 is not a symbolic link

/sbin/ldconfig.real: /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn_ops_train.so.8 is not a symbolic link

/sbin/ldconfig.real: /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn_cnn_train.so.8 is not a symbolic link

/sbin/ldconfig.real: /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn.so.8 is not a symbolic link

```



解决方法：

```
(base) root@rtx2060:/home/simple/Desktop#
(base) root@rtx2060:/home/simple/Desktop# sudo ln -sf /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn_adv_infer.so.8.9.0 /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn_adv_infer.so.8
(base) root@rtx2060:/home/simple/Desktop# ln -sf /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn_adv_train.so.8.9.0 /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn_adv_train.so.8
(base) root@rtx2060:/home/simple/Desktop# ln -sf /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn_cnn_infer.so.8.9.0 /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn_cnn_infer.so.8
(base) root@rtx2060:/home/simple/Desktop# ln -sf /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn_cnn_train.so.8.9.0 /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn_cnn_train.so.8
(base) root@rtx2060:/home/simple/Desktop# ln -sf /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn_ops_infer.so.8.9.0 /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn_ops_infer.so.8
(base) root@rtx2060:/home/simple/Desktop# ln -sf /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn_ops_train.so.8.9.0 /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn_ops_train.so.8
(base) root@rtx2060:/home/simple/Desktop# ln -sf /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn.so.8.9.0 /usr/local/cuda-11.8/targets/x86_64-linux/lib/libcudnn.so.8
(base) root@rtx2060:/home/simple/Desktop# sudo ldconfig
(base) root@rtx2060:/home/simple/Desktop#
```

# Reference

https://blog.csdn.net/Zhou_Dao/article/details/114229829

