# Running Pre-build Project
## Steps=>
### First Four steps are same as building project from scratch
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
 
 5] Now download the Project.rar file from here https://drive.google.com/file/d/1PgXG13vUNIofIlw480FAM_Y8ybLxdo66/view?usp=drive_web
 
 6]Extract the folder you'll get data & Models folder. Replace these folders at below location
 
 >Jetson-inference/python/training/classification/
 
 7]Directly test the project

use this command to test cancer model <br />

>imagenet --model=models/ct-scan/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=data/ct-scan/labels.txt data/Project/Test01/Input/mix data/Project/Test01/Output

Use this command to test x-ray model <br />

>imagenet --model=models/xray/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=data/xray/labels.txt data/Project/Test02/Input/mix data/Project/Test02/Output

For live detection<br />
cancer model <br />

>imagenet --model=models/ct-scan/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=data/ct-scan/labels.txt /dev/video0

X-ray model <br />

>imagenet --model=models/xray/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=data/xray/labels.txt /dev/video0
