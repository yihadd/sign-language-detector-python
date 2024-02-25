# Sign language detection python🐍
![img1](https://github.com/yihadd/sign-language-detector-python/assets/141911690/08c02fe1-d98b-498f-a768-c86b47c7e2ce)
## first you have to install these requirement
- open CV
- media Pipe
- scikit-learn

# the process of these project

1. Data preparation 
2. Data creation 
3. Train the model
4. test how this model perform

# Collecting image
- we will a code to collect the image
- this script will help us to create our dataset
- it will working with a webcam —> it will collect many different sample of three symbol A, B, and L (100 image)
- because we building a classifier and the way classifier work   —> need a data —> more data — is going to be much more better
- in this case we will crop the hand frame on the image or you can take a landmark on your hand
![letterA](https://github.com/yihadd/sign-language-detector-python/assets/141911690/747d5c94-e0e5-4647-bd42-a59d893dcd2b)
![letterB](https://github.com/yihadd/sign-language-detector-python/assets/141911690/3ba5087e-32fe-4523-97c6-1746f25712ea)
![letterL](https://github.com/yihadd/sign-language-detector-python/assets/141911690/b846ef0e-3d12-4835-95ca-9c96c6a8be6c)

# Create dataset
- in these code we trying to create dataset of hand gesture
- this code is like a data collector for hand gestures. It takes pictures, finds hands in them, remembers the hand positions, and labels them based on the gesture

## step in in these process

1. setting up the tool:
- import libraries like os —> to work with files, pickle —> to save a data, Mediapipe —> for detecting hand and other for processing images

## then collecting data:

- it looking through a folder filled with picture of hand(gesture)
- for each picture
1. it pinpoint important point on the hand (like fingertip)
2. it remember these point and label them base on the gesture in picture(like one finger up, all finger down, and four finger up)

## finally 

- it store all data the collect hand information and their label in a file name “data.pickle”
- these file will be use later for train a data in next step

# Training 
- we load a previous saved “data.pickle file” that contain feature and label
- split the data into 80% for train and 20% for testing
- using Random forest classifier by using train data, allow it to learn relationship between feature an label
- then use train model to predict label for unseen testing data
- lastly, save the model. allow predicting on new data without retraining.
## why we have to split
- to prevent “Overfitting” it happen when a model memorize the train data “too well”(like train 100%) it leading to poor performance on unseen data.
- by splitting the data to make sure the model learn “general pattern” instead of focusing on specific detail.
- by splitting the data to make sure the model learn “general pattern” instead of focusing on specific detail.
## Random Forest classifies
![random](https://github.com/yihadd/sign-language-detector-python/assets/141911690/4605598a-2c68-4523-b9c2-49070d8316bb)
- it like a group of student(each student call decision tree)
- and it look it the different feature(ex: hand position , finger angle, number of finger extended, distance between finger) and make a guess about the categories
- the final prediction is base on “Majority vote” of student

## in this case 

- Feature : hand position, finger position, finger angle, movement pattern
- Label: A,B,L base on hand feature

# Testing the result

- in this step going to detecting hand gesture in real-time
- and predict specific character (A,B,L)
- load a pre-train “data.pickel”

## step of process

- convert the frame from BGR to RGB
- detect hand in the frame

## for detecting hand 

- draw landmark on the hand
- extract X and Y coordinate on landmark
- prediction and display.
  ![handB](https://github.com/yihadd/sign-language-detector-python/assets/141911690/0296b912-d4c0-47dc-8a65-562be1009888)
