# TO-DO
* Get CO-DETR conversion working. Currently I'm not sure which functions are failing and need function rewriters.
    * Figure out how to get which functions are failing in torch2onnx conversion.
    * Check out [this](https://github.com/open-mmlab/mmdeploy/pull/2410) PR which shows adding DINO support.

### run command :
```bash
python3 tools/torch2onnx.py configs/mmdet/detection/detection_tensorrt-fp16_dynamic-320x320-1344x1344.py ../mmdetection/projects/CO-DETR/configs/codino/co_dino_5scale_swin_l_16xb1_16e_o365tococo.py co_dino_5scale_swin_large_16e_o365tococo-614254c9.pth ../mmdetection/demo/demo.jpg --work-dir trt_logs --device cuda:0 --log-level 'DEBUG'
```

### docker command :
```bash
sudo nvidia-docker run --shm-size=2gb --network=host -v /home/ganesh/mmdeploy:/root/workspace/mmdeploy -v /var/run/docker.sock:/var/run/docker.sock --rm -ti openmmlab/mmdeploy:ubuntu20.04-cuda11.8-mmdeploy1.3.1  /bin/bash
```

Right now I can't get verbose outputs which show which layers are failing the onnx export. Have asked on the discord but no response yet. 
## Next steps:
* Try building model little by little, backbone, neck etc. and try exporting. 