# Human-Activity-Recognition-Multiheaded-Cnn-Lstm

A model to predict human actions based on some classes using smartphone or on general sensors data. HAPT dataset is used here that comprises of accelerometer data and gyroscope data that were precprocessed using noise filters.Using this architecture to classify actions, we get an accuracy of 99 % with almost all classes identified correctly.
CNN is used to extract features from input data sequence and then LSTM is used so as to use power of LSTM's that are very good in time series prediction and classification task.
After final training of this model, we got only abount 20 classes wrong among 2005 test data inputs, giving an accuracy of about 99%.

Dataset is an extended version of UCI HAR Dataset. It is divided into two parts, one contain 561-feature vector as each input and its corresponding output and other has raw data collected from inertial sensors at 50Hz. Here, raw data is used to extract a window size of 128 with two different overlapping sizes according to class frequency.

A video of experiment can be seen in following link :- http://www.youtube.com/watch?v=XOEN9W05_4A

Prediction is made corresponsing to 12 classes :-
1. WALKING           
2. WALKING_UPSTAIRS  
3. WALKING_DOWNSTAIRS
4. SITTING           
5. STANDING          
6. LAYING            
7. STAND_TO_SIT      
8. SIT_TO_STAND      
9. SIT_TO_LIE        
10. LIE_TO_SIT        
11. STAND_TO_LIE      
12. LIE_TO_STAND      

## Steps :-

### Data preperation :-
- Data is loaded from corresponding directories and a window size of 128 is extracted along with their corresponding labels.
- Last 6 classes were actually derived from original classes and it does not have much data, so more overlapping is used for them.
- Missing values if any are removed and dataset is splitted into 3 parts 70%, 15%, 15% for training, testing and validation resp.
- Minmax scaler (range -1 to  1) object is fitted on trained data and then applied on all datasets.
- Classes vector are one-hot encoded.

### Building and training model :-
- Two CNN head each corresponging to a sensor data is build and their outputs are concatenated and passed to LSTM block.
- Layer normalization and Dropouts are used.
- Total trainable parameters = 69,444

- Training is preformed for 200 epochs, 100 batch size and Adam optimizer with decreasing learning rate.
  - Training accuracy obtained = 99.87 %
  - Validation accuracy obtained = 98.70 %

- Training is performed again for 100 epochs but with AdaGrad optimizer.
  - Training accuracy obtained = 99.97 %
  - Validation accuracy obtained = 98.90 %


Training curves obtained are as follows:- 

![download](https://user-images.githubusercontent.com/87748321/175473733-3ede7691-5c5d-4dfc-ab04-3c97757b3512.png)

Confusion matrix for testing data :- 

![download (1)](https://user-images.githubusercontent.com/87748321/175473809-c0dbc9a3-a2a2-40c2-be23-b6092e509ff6.png)

