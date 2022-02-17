# 2.5D-Resnet-Unet-for-fibula-segmentation
This is the instruction text for my master thesis project “Automatic segmentation of fibula bone by using deep learning”. The detail of this project can be found on our thesis and our defense PPT. This text only explains the code. The code and some files are on the github https://github.com/libeiyang/2.5D-Resnet-Unet-for-fibula-segmentation.


1.	Environment  
Google colab is main development environment. The official website is https://colab.research.google.com/.
Same with Python on the computer. In the Colab, you can just use   
		!pip install xxxxx
command to install the library which you needed. Because all the data is on the cloud, Google Drive is used for data storage. User should upload the data to the Google Drive first. Then use  
from google.colab import drive
		drive.mount("/content/drive")
to connect the colab with your google drive. After that, user can use
		/content/drive/MyDrive/xxxxxxx
as the path to read or write the data.  

2.	Data preprocessing  
In the segmentation.ipynb, section “data preprocessing” processed the original data to the npz format which can be read directly by Python. Almost all are annotated and you can understand what the codes do. The other section of segmentation.ipynb is used for Vnet framework which is failed. DO NOT LEARN THAT PART.  

3.	Dataloader  
Our dataloader is based on the Pytorch. In the Unet Pytorch.ipynb, section “Dataloader” shows how to construct a dataloader.   

4.	Unet  
We used SMP library to construct the main part of Resnet-Unet. The official website is https://segmentation-modelspytorch.readthedocs.io/en/latest/#. If you want to use this library, you should learn this website. Besides, you should learn the source code of this library.  
https://github.com/chsasank/segmentation_models.pytorch
This library is based on the Pytorch. In the source code, you will find many Pytorch API. So when you have something not clear, just check Pytorch source code.
In the section “Dataloader”, the train function constructs an Unet model and it shows how dataloader work with model, how to evaluate the model and how to test the model. Sometimes for some reason, such as RAM is not enough, the train cannot in once. The function “Continue train” is needed which can continue train the model.
In the section “final Dataloader for Sagittal” and “train for sagittal”, I used this method.
Another thing that needs to be mentioned is there are some sections which function are almost same, only some details are different. That is because we iterated our project many times or the codes are used for different plane. When you find some similar section, you can just learn the section which name includes “DA” or “final”. These are the last version of that part.  

5.	Combination  
Section “Merge sagittal”, you can find how to combine the result of sagittal. (For sagittal plane, we used CROI method to crop the fibula part. You can find this method in our thesis.) Section “Merge sagittal and axial” shows how to combine the result of different planes. All the combination is based on the Maximum probability combination.   

6.	Result analysis  
We used Average Dice loss and 3D Dice loss to evaluate our model. Function “evaluate” in section “final Dataloader for Sagittal” will tell you how to use these wo methods. We also visualized the dice scores of each CT slice. You can find it in the section “loss distribution axial”.   

7.	Others  
Other sections are as their name. Some sections are used for result visualization. Section “3D export” shows how to export the vtk or nii file. You can use ITK-SNAP or 3D slicer to check your result. Section “DA data” shows how to make data augmentation.  

I think that is what I can explain. If you have some difficult, you need to learn more Deep learning knowledge, Python programming and Pytorch. Some basic CV knowledge is also needed. For the network part, please learn the website and source code clearly as I said before.  

Hope this text can help you!  
My Email address is lby980804@gmail.com
  
