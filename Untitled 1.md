python 打印年月日，时分秒

```python
time.strftime('%Y/%m/%d %H:%M:%S')
```

----

无论用什么框架训练的模型，推荐转为onnx格式，方便部署。

支持onnx模型的框架如下：

- TensorRT：英伟达的，用于GPU推理加速。注意需要英伟达GPU硬件的支持。
- OpenVino：英特尔的，用于CPU推理加速。注意需要英特尔CPU硬件的支持。
- ONNXRuntime：微软，亚马逊 ，Facebook 和 IBM 等公司共同开发的，可用于GPU、CPU
- OpenCV dnn：OpenCV的调用模型的模块

pt格式的模型，可以用Pytorch框架部署。

推理效率上：TensorRT>OpenVino>ONNXRuntime>OpenCV dnn>Pytorch

由于电脑只有CPU，因此研究下OpenVino、ONNXRuntime、OpenCV dnn的C++使用。

【参考链接】https://www.cnblogs.com/xixixing/p/15830977.html

