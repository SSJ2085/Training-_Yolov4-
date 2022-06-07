# Training-_Yolov4
This Project is the steps to train any yolo algorithum for any custom dataset. we have trained our model on the yolov4 for the greyscale images. 
This project uses Darknet gothub repository for the pretrained model and for the configuration file for the yolo.
To train an yolo algorithm we need to follow the following steps:-

1. ## Installing Darknet and make some changes:
   git clone https://github.com/AlexeyAB/darknet.git
   cd darknet
   (Note you want GPU please follow the steps. Important GPU is needed to training otherwise not need)
   (Change the GPU 0 to 1 and save it. If you installed openCV set OPENCV 0 to 1 otherwise not need)
   
   For changing Run following command:
   !sed -i 's/OPENCV=0/OPENCV=1/g' Makefile
   !sed -i 's/GPU=0/GPU=1/g' Makefile
   !sed -i 's/CUDNN=0/CUDNN=1/g' Makefile
   !sed -i "s/ARCH= -gencode arch=compute_60,code=sm_60/ARCH= ${ARCH_VALUE}/g" Makefile
   
3. ## Create A Data Set:
   For the YOLO training to be execuited the dataset require file (jpg file and .txt file) the tect file include the class name and the coordinates of the block  
   labelled. this labelling can be done using the Labelimg.
   
4. ## Move Everything to Google Colab
   Move the prepared folder to your local Google drive directory.
   
5. ## Setting Up Colab:
    enable the GPU. So, click on “Edit” -> “Notebook settings”, select “GPU”, and click “SAVE
    
6. ## Check if gpu is enabled:
   ### CUDA: Let's check that Nvidia CUDA drivers are already pre-installed and which version is it.
   !/usr/local/cuda/bin/nvcc --version
   ### We need to install the correct cuDNN according to this output
   !nvidia-smi
   
7. ## Save weight during training in your Google Drive
   This step is important since COLAB environment will be recycle after 12 hours and all files locate in its working space will be deleted. Here link to save the   
   weight directly into backup folder which is created in GDrive before. In my case, backup folder directory is Drive/weight/backup.
   
8. ## create the .names file the data file.
    using the python script data_and_name.py
    
9. ## create the train and test txt file.
    using create_train_test.py

10. ## Finally, let's train our model
   !darknet/darknet detector train images/labelled_data.data darknet/cfg/yolov4_custom.cfg custom_weights/yolov4.conv.137 -dont_show 
       
       
       

