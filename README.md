# Yolov5 export to CPU
It is a two step process:

1. Convert model weights to tflite
2. Run the inference on CPU



### Convert Model Weights to tflite



**If you don't want to install anything on your system then use this [Google Colab](https://colab.research.google.com/drive/1oZN9azdFyrlbzeVcGaqdddJ_YVatVTJJ?usp=sharing) (*Recommended*).**  [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1oZN9azdFyrlbzeVcGaqdddJ_YVatVTJJ?usp=sharing)



##### And if you want to perform the conversion on your system then follow bellow instructions:

I recommend create a new conda environment for this as we need python==3.7.0 for this: 

```
conda create -n yolov5_env python==3.7.0
conda activate yolov5_env
```

Then run below commands and replace **yolov5s.pt** with your own model path and also change **yolov5s.yaml** accordingly. 

```bash
git clone https://github.com/karanjakhar/yolov5.git
cd yolov5
pip3 install tensorflow==2.3.1
pip install -r requirements.txt
python3 models/tf.py --weight yolov5s.pt --cfg models/yolov5s.yaml --img 416 
```



### Run the inference on CPU

If you have created conda environment in conversion step then activate it ( `conda activate yolov5_env` ) and follow below steps. Otherwise I recommend creating a conda environment: 

```
conda create -n yolov5_env python==3.7.0
conda activate yolov5_env
```

then follow below steps:

```bash
git clone https://github.com/karanjakhar/yolov5-export-to-cpu.git
cd yolov5-export-to-cpu
pip3 install -r requirements.txt
python3 yolov5_tflite_folder_of_images_inference.py --weights yolov5s-fp16.tflite --folder_path images/ 
```





**yolov5_tflite_inference.py**   this file contains main inference code which you can use with your own project. 

Other files show examples how to use it. I have placed a tflite file and some sample images to run a quick test. 





