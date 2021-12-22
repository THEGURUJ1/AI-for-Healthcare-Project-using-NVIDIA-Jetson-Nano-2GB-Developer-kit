# AI-for-Healthcare-Project-using-NVIDIA-Jetson-Nano-2GB-Developer-kit
![image](https://user-images.githubusercontent.com/80514108/147107654-c9d06d72-35a9-4a28-8d4a-d133eae3c282.png)

### This project uses Deep learning concept in detection of Various Deadly diseases. 
### It can Detect 1) Lung Cancer 2) Covid-19 3)Tuberculosis 4) Pneumonia. 
### It uses CT-Scan and X-ray Images of chest/lung in detecting the disease. 
### It has a Accuracy between 50%-80%. 
### It can take input in any Image format or through Live videos and provide accurate output results.
![image](https://user-images.githubusercontent.com/80514108/147101781-e98967f4-30fa-4a14-ab79-25999c7a4602.png)

## Attributions
### Using [@dusty-nv's](https://github.com/dusty-nv/) Jetson inference (https://github.com/dusty-nv/jetson-inference)
### Using these datasets
### 1)CT-Scan : https://www.kaggle.com/mohamedhanyyy/chest-ctscan-images/download
### 2)X-Ray   : https://www.kaggle.com/jtiptj/chest-xray-pneumoniacovid19tuberculosis/download

## Accessories & Resources

Jetson Developer Kit (2gb kit) <br />
Type C power (5V) supply <br />
Ethernet cable <br />
HDMI Cable <br />
Monitor with HDMI cable <br />
Camera (Logitech C270 HD WEBCAM) <br />
Keyboard & Mouse (wireless) <br />
Memory card (more than 32 GB) <br />
Optional: cooling fan, micro-USB cable(for headless mode) <br />
Jetson-Inference With Docker File: https://github.com/dusty-nv/jetson-inference <br />
Datasets: <br />
CT-Scan:-https://www.kaggle.com/mohamedhanyyy/chest-ctscan-images/download <br />
X-ray:-https://www.kaggle.com/jtiptj/chest-xray-pneumoniacovid19tuberculosis/download <br />

## Headings
### [Building Project from scratch](# building-project-from-scratch)
### [Running Pre-build Project](# running-pre-build-project)

# Building Project from scratch
## Steps=>
1] Gathering all the Accessories:- <br />
	We gathered all the Accessories mentioned above from the local market and collected 2GB Developer kit. <br /> 

2] Preparing for Setup:- <br />
	-connect SD card to PC/Laptop <br />
	-Download [SD card Image](https://developer.nvidia.com/jetson-nano-2gb-sd-card-image) (For 2 GB kit) <br />
	-Download [SD Card Formatter](https://www.sdcard.org/downloads/formatter/eula_windows/SDCardFormatterv5_WinEN.zip) & Install it. <br />
  ![image](https://user-images.githubusercontent.com/80514108/147107830-790d327b-c4cf-4b87-91a9-398530a1e3be.png) <br />
  -Quick format the SD card <br />
  ![image](https://user-images.githubusercontent.com/80514108/147108065-0bf320dc-7a7c-46d1-b39e-65a891c43d96.png) <br />
  -Download , Install & Launch [ETCHER](https://www.balena.io/etcher/) <br />
  ![image](https://user-images.githubusercontent.com/80514108/147108297-489c360b-249a-4a3d-8637-603ec45bbbc5.png) <br />
  -Select Downloaded image, select target device as Memory card then flash ( takes more than 10 min) <br />
3] Setting up Kit:- <br />
 Insert the SD card in kit <br />
 ![image](https://user-images.githubusercontent.com/80514108/147108494-d7900f4c-c6b4-423a-8ee4-90c772b4c4fc.png) <br />

Attach the Accessories in slots of kit as shown below <br />
![image](https://user-images.githubusercontent.com/80514108/147108671-0eb1690e-1236-4ce9-aedd-3505d308b086.png) <br />
![image](https://user-images.githubusercontent.com/80514108/147118733-b44666f5-a307-4978-a292-947a4c3be5a4.png) <br />

- Turn On power supply & wait for system to boot <br />
- When you boot the first time, the developer kit will take you through some initial setup, including: <br />
  - Review and accept NVIDIA Jetson software EULA <br />
  - Select system language, keyboard layout, and time zone <br />
  - Create username, password, and computer name <br />
  - Optionally configure wireless networking <br />
  - Select APP partition size. It is recommended to use the max size suggested <br />
  - Create a swap file. It is recommended to create a swap file <br />



3] Welcome screen:- <br />
![image](https://user-images.githubusercontent.com/80514108/147119806-70cfad4d-cb39-456e-82fe-9018626d08e0.png) <br />

4] Downloading Jetson Inference with Docker Container:- <br />

Open Terminal and type following command <br />
  >git clone --recursive https://github.com/dusty-nv/jetson-inference <br />

Wait until it downloads the container( May take 10-15 mins on slow connection) <br />
Change Directory to jetson-inference using below command <br />

  
  >cd jetson-inference <br />

Run the Docker container command, It will ask for the password of your kit. Enter password(in Linux the password you type is not shown) and press enter <br />
  
  >docker/run.sh <br />

It may take time in First time running the docker command and ask for models that you want to download. Download default models and presss ok <br />

![image](https://user-images.githubusercontent.com/80514108/147123139-56cee00b-19bb-4757-aa5f-a4f8eda5bbf4.png)
 <br />
 
 5] Now download the trained dataset from kaggel, we used the following datasets:- <br />

CT-Scan:-https://www.kaggle.com/mohamedhanyyy/chest-ctscan-images/download <br />
X-ray:-https://www.kaggle.com/jtiptj/chest-xray-pneumoniacovid19tuberculosis/download <br />
 <br />
  -  CT-Scan:- <br />
It has CT-scan Images of lung of Cancer Patients and Normal People <br />
![image](https://user-images.githubusercontent.com/80514108/147123461-233fc55e-a1e9-410c-a9a4-d497dde7c024.png) <br />

- X-ray:- <br />
This dataset consist of lung x-ray images of Covid-19 patient, Pneumonia patient, Tuberculosis patient and Normal people <br />
![image](https://user-images.githubusercontent.com/80514108/147123632-dcd64bcd-41f5-4087-9cfd-2e2e55ff1ff7.png)
 <br />
 Now Extract the dataset in location:  <br />

>Jetson-inference/python/training/classification/data/ 

With dataset name. In that folder create a label.txt file and name all the things that your kit gonna detect
 <br />
 ![image](https://user-images.githubusercontent.com/80514108/147123952-100f7ccb-e01d-48b7-83a1-4cd19ffda1aa.png)
 <br />
 
 6] Training our Dataset:- <br />
Enter following command <br />

>python3 train.py --model-dir=models/ct-scan --batch-size=4 --workers=1 --epochs=35 data/ct-scan

 <br />It will take around 8-10 hours for training and Kit gets hot so don’t touch it.

 <br />7] Now export the trained model in onnx file

>python3 onnx_export.py --model-dir=models/ct-scan

 <br />8] Do the same thing with other dataset
 <br />9]Now test the project:-

> imagenet --model=models/ct-scan/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=data/ct-scan/labels.txt (input location) (Output location)

 <br />For  webcam based detection:
 
 >imagenet --model=models/ct-scan/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=data/ct-scan/labels.txt  /dev/video0

 <br />
 10] you can Train the model once more to increase the accuracy or Go ahead and try it with different models to create awesome project. For any help Contact:- abhishekbhandare92@gmail.com
 <br />
 

 ## Model Accuracy
 ![Untitled design (1)](https://user-images.githubusercontent.com/80514108/147124505-ba8e6359-cf02-48a2-9fb4-5beb4f25f280.png)
  <br />
  ![Untitled design](https://user-images.githubusercontent.com/80514108/147124597-2d6ab1a3-60a0-475f-ab55-248bd303fc52.png)

   <br />
   
# Resources
We have enclosed all the project required and processed files in the folder. <br />
Replace this data folder with jetson-inference/python/training/classification/data <br />
& <br />
Models folder with <br />
>jetson-inference/python/training/classification/models
 <br />

![image](https://user-images.githubusercontent.com/80514108/147124823-dbde53e9-de3a-4494-a845-8241f6f6f005.png)


# Running Pre-build Project
### First Four steps are same 
1] Gathering all the Accessories:- <br />
	We gathered all the Accessories mentioned above from the local market and collected 2GB Developer kit. <br /> 

2] Preparing for Setup:- <br />
	-connect SD card to PC/Laptop <br />
	-Download [SD card Image](https://developer.nvidia.com/jetson-nano-2gb-sd-card-image) (For 2 GB kit) <br />
	-Download [SD Card Formatter](https://www.sdcard.org/downloads/formatter/eula_windows/SDCardFormatterv5_WinEN.zip) & Install it. <br />
  ![image](https://user-images.githubusercontent.com/80514108/147107830-790d327b-c4cf-4b87-91a9-398530a1e3be.png) <br />
  -Quick format the SD card <br />
  ![image](https://user-images.githubusercontent.com/80514108/147108065-0bf320dc-7a7c-46d1-b39e-65a891c43d96.png) <br />
  -Download , Install & Launch [ETCHER](https://www.balena.io/etcher/) <br />
  ![image](https://user-images.githubusercontent.com/80514108/147108297-489c360b-249a-4a3d-8637-603ec45bbbc5.png) <br />
  -Select Downloaded image, select target device as Memory card then flash ( takes more than 10 min) <br />
3] Setting up Kit:- <br />
 Insert the SD card in kit <br />
 ![image](https://user-images.githubusercontent.com/80514108/147108494-d7900f4c-c6b4-423a-8ee4-90c772b4c4fc.png) <br />

Attach the Accessories in slots of kit as shown below <br />
![image](https://user-images.githubusercontent.com/80514108/147108671-0eb1690e-1236-4ce9-aedd-3505d308b086.png) <br />
![image](https://user-images.githubusercontent.com/80514108/147118733-b44666f5-a307-4978-a292-947a4c3be5a4.png) <br />

- Turn On power supply & wait for system to boot <br />
- When you boot the first time, the developer kit will take you through some initial setup, including: <br />
  - Review and accept NVIDIA Jetson software EULA <br />
  - Select system language, keyboard layout, and time zone <br />
  - Create username, password, and computer name <br />
  - Optionally configure wireless networking <br />
  - Select APP partition size. It is recommended to use the max size suggested <br />
  - Create a swap file. It is recommended to create a swap file <br />



3] Welcome screen:- <br />
![image](https://user-images.githubusercontent.com/80514108/147119806-70cfad4d-cb39-456e-82fe-9018626d08e0.png) <br />

4] Downloading Jetson Inference with Docker Container:- <br />

Open Terminal and type following command <br />
  >git clone --recursive https://github.com/dusty-nv/jetson-inference <br />

Wait until it downloads the container( May take 10-15 mins on slow connection) <br />
Change Directory to jetson-inference using below command <br />

  
  >cd jetson-inference <br />

Run the Docker container command, It will ask for the password of your kit. Enter password(in Linux the password you type is not shown) and press enter <br />
  
  >docker/run.sh <br />

It may take time in First time running the docker command and ask for models that you want to download. Download default models and presss ok <br />

![image](https://user-images.githubusercontent.com/80514108/147123139-56cee00b-19bb-4757-aa5f-a4f8eda5bbf4.png)
 <br />
 
 
 



  

