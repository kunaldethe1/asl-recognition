![image](https://github.com/kunaldethe1/asl-recognition/assets/64221339/f6256a3f-d2ee-42d3-897b-3ccd1fcee91a)# asl-recognition
Developing a tool to convert sign language to text

**Summary**
This project involved the design and implementation of a convolutional neural
network model using tensorflow and opencv to extract images
features from a database of over 15000 self created images. 
Further, Python was used to create two layers of algorithm to correctly
predict sign language in real time.
Created confusion matrices to further improve prediction accuracy to a final of 95.4%. 
Used hunspell library to facilitate word and sentence suggestion.

**Directory Organization**
A Python script utilizing the os and string modules was developed to create a directory structure for the 'dataset.' 
The 'dataset' directory serves as the parent directory and contains two subdirectories: 'training_data' and 'testing_data.'
Each of these subdirectories further consists of 26 folders, representing the 26 letters of the alphabet.
These individual folders will later be populated with images to facilitate the training and testing of the data.


**Data Collection**


![image](https://github.com/kunaldethe1/asl-recognition/assets/64221339/a41b10d2-ff8e-4d5a-ba0a-74a36e72531e)
A script was developed to capture sign language gestures using OpenCV and computer vision. It involves initializing data collection settings, accessing webcam feed, mirroring frames, displaying gesture image counts, defining a capture area, processing the captured gesture, displaying the processed image, and saving images based on user input.
The image is saved in the folder of the corresponding letter pressed.
There's an image counter for each letter on the left side of the camera display (as seen in the image above).
Same was done for testing and validation datasets.

Different filters were tried onto the Region of Interest (ROI) to find the most suitable one for feature extraction.

![image](https://github.com/kunaldethe1/asl-recognition/assets/64221339/8a0894aa-f8f6-4a45-b998-d07f5d585552)

**Building the CNN**
![image](https://github.com/kunaldethe1/asl-recognition/assets/64221339/b8df0326-6965-4ee9-ac0c-96890f49cc0b)

![image](https://github.com/kunaldethe1/asl-recognition/assets/64221339/a31c1414-6736-4363-a52f-8145f9b1551e)
![image](https://github.com/kunaldethe1/asl-recognition/assets/64221339/52d7ffe8-04e8-400e-8158-c791274f6035)


The model.ipynb file runs the creation of the sequential model:
The model architecture consists of various layers: a Conv2D layer with 32 filters and a (3, 3) kernel size processes an input of shape (128, 128, *), where * represents input image channels. A MaxPooling2D layer with (2, 2) pooling reduces spatial dimensions. Another Conv2D layer follows, similar to the first. This is succeeded by another MaxPooling2D layer. A Flatten layer converts output into a 1D array for fully connected layers. Three dense layers are employed, with 128, 96, and 64 units, respectively, applying ReLU activation. Dropout layers, following dense layers, help prevent overfitting by randomly deactivating inputs during training.

**Model Summary**
![image](https://github.com/kunaldethe1/asl-recognition/assets/64221339/3a1e8de0-5039-4651-8028-977e178f19c5)

![image](https://github.com/kunaldethe1/asl-recognition/assets/64221339/7c0ae358-bcfa-4855-a709-3d03f1c144d0)

Algorithm Layer 1:
I.	Apply gaussian blur filter and threshold to the frame taken with opencv to get the processed image after feature extraction.
II.	This processed image is passed to the CNN model for prediction and if a letter is detected for more than 50 frames then the letter is printed and taken into consideration for forming the word.
III.	Space between the words is considered using the blank symbol.
The main prediction is made by the predict method that resizes an input image and uses loaded model to make predictions. The predicted values are stored in a dictionary, sorted based on their values, and the most probable symbol is assigned to the self.current_symbol variable.
This represents the first layer of the application. 
![image](https://github.com/kunaldethe1/asl-recognition/assets/64221339/889df9b9-bbcf-4115-a321-fddc5e218681)

Based on the confusion matrix: {D, R, U}, {T, K, D, I}, {S, M, N} were the three sets of letters with increased similarity and overlap in terms of accuracy.
By training three dedicated classifiers specific to these sets, it was anticipated that the accuracy of classification for these symbols would improve.
![image](https://github.com/kunaldethe1/asl-recognition/assets/64221339/bab11029-d3a2-4c1a-922e-2b771105169a)


**Final Accuracy**

![image](https://github.com/kunaldethe1/asl-recognition/assets/64221339/44049183-1ef0-48c3-9bb1-73376c0a65dc)

The model correctly classified approximately **95.45%** of the testing instances. 

**GUI**

Finally, the GUI was implemented using the tkinter library in python.
![image](https://github.com/kunaldethe1/asl-recognition/assets/64221339/9d3cea50-00c6-40d7-aa21-28cf77dfd179)
