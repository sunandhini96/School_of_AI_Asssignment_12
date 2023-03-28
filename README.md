# School_of_AI_Asssignment_12

## Yolo V3 Object detection :

## Task 1) By using Open Cv Yolo V3 code :

Code : https://github.com/sunandhini96/School_of_AI_Asssignment_12/tree/main/Yolov3_object_detection

I ran the code on google colab by taking an image of myself, holding Bottle object which is there in COCO data set. 

coco.names --> class names in the dataset

yolov3.cfg --> configuration file

yolov3_object_detection.ipynb : code (using readNetFromDarknet code)

WIN_20230325_08_18_44_Pro.jpg --> Input image

![WIN_20230325_08_18_44_Pro](https://user-images.githubusercontent.com/63030539/227792704-e5160837-1bf9-4133-9e0c-9914763e56b4.jpg)

annotated_image.png --> output image

<img width="404" alt="image" src="https://user-images.githubusercontent.com/63030539/227792835-6917acc0-f5b8-4e86-b82c-f84d30c37695.png">

yolov3 task 1 --> ( using readNet code)

https://github.com/sunandhini96/School_of_AI_Asssignment_12/blob/main/Yolov3_object_detection/yolov3_object_detection_task1.ipynb

WIN_20230325_08_18_44_Pro.jpg --> Input image

![WIN_20230325_08_18_44_Pro](https://user-images.githubusercontent.com/63030539/227792704-e5160837-1bf9-4133-9e0c-9914763e56b4.jpg)

annotated_image_task1.png --> output image

<img width="383" alt="annotated_image_task1" src="https://user-images.githubusercontent.com/63030539/228132914-5a61789d-3bf7-4013-9ed4-b7bfefdb1069.png">


## The implementation steps for YOLOv3 :

i) Set up the environment: Install necessary dependencies such as opencv,pytorch.

ii) Download the YOLOv3 weights,YOLOv3 configuration file and coco names file.

iii) Load the pre-trained weights,configuration file.

iv) Set up the pre-processing steps such as resizing and normalization.

v) Define the post-processing steps for the model's output, such as non-maximum suppression (NMS), thresholding, and bounding box decoding.

vi) Running the YOLOv3 model on the input images and obtain the detection results.

vii) Visualize the detection results.

## Task 2) : Training YoloV3 on custom dataset

All the files are presented in this folder -->  https://github.com/sunandhini96/School_of_AI_Asssignment_12/tree/main/YoloV3

Custom datset : Each class consists of 25 images. We created 4 classes ( 100 images).

4 classes : Lion, Mr.bean, Ship, Mickey Mouse.

We annotated the images by using Yolo V3 annotation tool : https://github.com/miki998/YoloV3_Annotation_Tool

By following the steps in https://github.com/theschoolofai/YoloV3 repository.

We trained Custom datset of YoloV3 for 300 epochs.

After training the YoloV3 model, we observed detecting the objects by running detect.py .

Output for last few epochs: 

 Epoch   gpu_mem      GIoU       obj       cls     total   targets  img_size
   295/299       12G     0.975     0.397     0.108      1.48        25       512: 100% 9/9 [00:01<00:00,  6.70it/s]
               Class    Images   Targets         P         R   mAP@0.5        F1: 100% 1/1 [00:00<00:00,  1.86it/s]
                 all        10        10     0.736         1     0.953     0.841

     Epoch   gpu_mem      GIoU       obj       cls     total   targets  img_size
   296/299       12G      1.14     0.358    0.0559      1.56        15       512: 100% 9/9 [00:01<00:00,  6.65it/s]
               Class    Images   Targets         P         R   mAP@0.5        F1: 100% 1/1 [00:00<00:00,  1.78it/s]
                 all        10        10     0.735         1     0.953     0.841

     Epoch   gpu_mem      GIoU       obj       cls     total   targets  img_size
   297/299       12G      0.92     0.429    0.0618      1.41        29       512: 100% 9/9 [00:01<00:00,  6.93it/s]
               Class    Images   Targets         P         R   mAP@0.5        F1: 100% 1/1 [00:00<00:00,  1.83it/s]
                 all        10        10     0.736         1     0.953     0.841

     Epoch   gpu_mem      GIoU       obj       cls     total   targets  img_size
   298/299       12G     0.908     0.386      0.12      1.41        24       512: 100% 9/9 [00:01<00:00,  6.91it/s]
               Class    Images   Targets         P         R   mAP@0.5        F1: 100% 1/1 [00:00<00:00,  1.85it/s]
                 all        10        10     0.738         1     0.953     0.842

     Epoch   gpu_mem      GIoU       obj       cls     total   targets  img_size
   299/299       12G     0.934     0.376    0.0429      1.35        23       512: 100% 9/9 [00:01<00:00,  6.88it/s]
               Class    Images   Targets         P         R   mAP@0.5        F1: 100% 1/1 [00:00<00:00,  1.84it/s]


We created video by following some steps : 

## Task 3 : Video Creation:

First trained yoloV3 model on custom dataset (with 4 classes - lion, ship, mr.bean,Mickeymouse).

Download a very small (~10-30sec) video from youtube which shows our classes.
 
by using ffmpeg to extract frames from the video. 

 !ffmpeg -i video.webm -f image2 image-%03d.png
 
 By running detect.py to infer the images.
 
!python detect.py --source "/content/drive/MyDrive/sunandini/YoloV3/images" --weights "/content/drive/MyDrive/sunandini/YoloV3/weights/last.pt" --cfg "/content/drive/MyDrive/sunandini/YoloV3/data/cfg/yolov3-custom.cfg" --conf-thres 0.3 --output "/content/output_16_images"

By using ffmpeg  to convert the files in your output folder to video

!ffmpeg -i image-%03d.png video_1.mp4

Uploaded the video to YouTube. 

Here link for the Youtube Video :

https://www.youtube.com/watch?v=jDCcqkfNNLo


Output of 16 images (4 images for each class) :

https://github.com/sunandhini96/School_of_AI_Asssignment_12/tree/main/YoloV3/Output_16_images

<img width="1007" alt="image" src="https://user-images.githubusercontent.com/63030539/227793544-609d3655-54c4-41e1-8198-9e16cb9cb7c2.png">



