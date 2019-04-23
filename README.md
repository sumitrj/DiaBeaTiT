# DiaBeaTiT: 
<b><i><u>Blood Sugar prediction using Saliva</b></i></u>

## Defining the Problem:

<b>Diabetes is a long-term condition that causes high blood sugar levels. Treatment requires:</b>

1. Tracking and monitoring of blood sugar level at uniform and frequent intervals.

2. Doing appropriate physical exercise, undertaking appropriate diet, controlling stress levels.

3. Taking insulin doses regularly.

<b>Inconveniences faced by Patients and Doctors in the treatment procedure:</b>

1.  Blood Sugar tracking is an invasive process, it requires person’s blood to calculate glucose level. There is a need for changing the blood sample collecting plate for every test which makes the system even more expensive.

2.  The discomfort of pain and risk of infection can sometimes be a source of great stress and concern.
    
3.  No facility to check glucose level in remote areas without a proper setup.
    
## Approach to solve the Problem:

<b>Non Invasive Blood Glucose level Calculation using saliva </b> 
  
Step 1:
Establish theoretically, the effect of variation of blood glucose level on parameters of chemical, electrical or optical parameters of saliva and urine.

Step 2:
Generate the data set of the variations in selected parameters from Step 1 and blood glucose level.

Step 3:
Analyse the data of Step 2 to find correlation. 

## Construction of the Device

<i> <u> <b>Part A: Construction of the Spectrometer </i> </u></b>

Near IR range LEDs (940nm) and photodiodes are placed opposite to each other considering an optical rotation of 180 degrees. 

These LED's are connected to <u>Arduino NANO </u> which is transferring data to <u>Raspberry Pi zero </u>.

A python script running on <u>raspberry pi zero </u>  uploads  these values to firebase.

<b> Callibration</b>

The intensity of emisstter LEDs is kept constant.

With variation in sample solution, the intensity of radiation at the other end of photodiode varies.

70 samples of known glucose concentration are placed in the device and attenuation metric is recorded.

According to Beer's Law, concentration and attanuation vary linearly hence, linear regression analysis is done to map attenuation values to concentration.  

Cs(A) = mA + b where Cs is concentraion of solution, A is the attenuation metric.

Range of A: 0 to 1023

<b>Weights after Regression Analysis:</b>
m = 2.69
b = - 1821.77

<b><i> <u> Part B: Glucose Level Prediction </i> </u></b>

Samples of saliva and blood of 100 people were collected and data was analysed. 

Information Entropy Analysis was found to be the perfect tool considering this to be a small sample data. 

Accuracy of 97.4% was achieved

The linear regression alternative of the algorithm had the following model:

BGL(Cs) = n*(Cs) + d

where BGL is Blood Glucose Level and Cs is the Glucose Concentration of Solution

<b>Weights after Regression Analysis:</b>
m = 27.69
b = 95.67

Hence, overall mathematical model is presented as:

<b> BGL(A) = 74.539*(A) - 174173.96439
where A is the attenuation metric

<i> <u><b> Part C: Cloud Interface </i> </u></b>

Cloud Tool : Firebase

The attenuation values are sent to firebase and an app interface is used to view the Blood Glucose Level.

