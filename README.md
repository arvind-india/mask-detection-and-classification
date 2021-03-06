# Mask Detection and Classification | Mask or No Mask detection | Deep Learning and Computer Vision

A deep understanding of the current COVID-19 pandemic shows how one person's negligence can cause widespread harm. Since the general public is getting back on the streets and employees going back to their workplaces, it is extremely important for everyone to adorn face-masks as suggested by WHO, to keep themselves and others safe. [WHO: value of masks](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/advice-for-public/when-and-how-to-use-masks)

The application detects persons faces and classifies if they are wearing a mask, or not. It shows a bounding box in the video feed and classifies the faces in the frame. 

### Here is a demo containing the application output: 
![enter image description here](https://github.com/iamsashank09/mask-detection-and-classification/blob/master/outputs/GIFoutput_video.gif)

![enter image description here](https://github.com/iamsashank09/mask-detection-and-classification/blob/master/outputs/output_P1.gif)

![enter image description here](https://github.com/iamsashank09/mask-detection-and-classification/blob/master/outputs/output_P2.gif)


### How to use the application:

The maskDetectionApp.py file contains the code to run the application. Before which, you need to download the trained model from [HERE](https://drive.google.com/open?id=19TwyycoDwUVJ3DWdsHJGbOXIgp8nvn2e) and place it in the folder "models". Example: "models/Res18oneFC_model.pth"

##### Running it on live webcam feed:

    python3 maskDetectionApp.py

##### Running it on a video:

    python3 maskDetectionApp.py video

Then the program will ask for the path of the video, please pass the path to the video file and the output will be saved in the "outputs" folder.

### Data, Model Architecture and Training:
You will find the training notebook at [MaskDetectionNet.ipynb](https://github.com/iamsashank09/mask-detection-and-classification/blob/master/MaskDetectionNet.ipynb) in the repository.
##### Data
The Dataset I've used is from the Eden Social Welfare foundation, Taiwan. Link in the resource section.
The dataset contains pictures of people wearing medical masks along with XML files containing their descriptions. The XML files contain their locations and labels _good, none_ or _bad_. I've ignored the *none* and only used the good and bad images.
I haven't included data pre-processing in the notebook. 

##### Implementation:

 - I used [PyTorch](https://pytorch.org/) to implement my network. This is my first
   experience with PyTorch and it has been swift and easy.
- I trained a Convolutional Neural Network for image classification using Transfer Learning.
- The architecture used is ResNet18, with a new Fully Connected layer.
- I downloaded the ResNet18 model with it's pre-trained parameters from the `torchvision.models` module.
- Then I froze the entire network except the 4th and the Fully connected layers by using `requires_grad == False` to freeze the parameters. 
- Trained the model on a GPU for `20 EPOCHS` and `BATCH_SIZE = 20` while tweaking the learning rate, arriving at a close to 99% accuracy. 



### Concerns over such monitoring applications:
As with my previous project on [Social Distance monitoring application](https://github.com/iamsashank09/social-distance-dashboard).
While working on this project, I started having concerns over how this kind of monitoring can be used to create spaces with no freedom, which is scary. I understand this kind of work can be used to boost authoritarianism and force suppression. I can only hope we always keep in mind the freedoms of the individual while we build a safe society.  


### Resources:
The [Medical Mask Dataset](https://www.kaggle.com/vtech6/medical-masks-dataset) from Kaggle.

Input video used for testing and development: [CBS17 Youtube](https://www.youtube.com/watch?v=VCR6lzXPy2A)

