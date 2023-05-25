# 自训练模型pt转onnx

> 模型 ：yolov5-v7.0
> 转换环境：yolov5-6.2
> windows 10 ， CPU

原始 pt 推理

```
python detect.py --weights weights\YOLOv5s_gesture\weights\best.pt --source 0
# 运行结果
Speed: 1.2ms pre-process, 232.7ms inference, 0.6ms NMS per image at shape (1, 3, 640, 640)
```



导出为 onnx；
```
python export.py --weights ./weights/YOLOv5s_gesture/weights/best.pt --img 640 --batch 1
```

验证导出的onnx是否正常；
```
python detect.py --weights weights\YOLOv5s_gesture\weights\best.onnx --source 0
# 运行结果
Speed: 1.8ms pre-process, 159.0ms inference, 1.1ms NMS per image at shape (1, 3, 640, 640)
```

导出为 IR

```
python export.py --weights ./weights/YOLOv5s_gesture/weights/best.pt --include openvino
```

验证导出的 IR 是否正常；

```
python detect.py --weights weights\YOLOv5s_gesture\weights\best_openvino_model\ --source 0
# 运行结果
Speed: 1.8ms pre-process, 129.0ms inference, 0.5ms NMS per image at shape (1, 3, 640, 640)
```

