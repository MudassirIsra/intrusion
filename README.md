# intrusion
## VA Cloud Data
### - Run this command 
```
python get_va_cloud_data.py –h
```
There is an optional argument naming “-cfg”. This argument take value as name of json file like “config.json”. The default name is “config.json” in the code. If you have json file with some other names like “config_v2.json” or “config_v1.json” you have to pass -cfg argument with your spacified name of json file. e.g
```
python  get_va_cloud_data.py -cfg “config_v2.json”
```
##### - Note : If your json file name is already “config.json” there is no need to pass -cfg argument
There are two positional argument {camera, model}. To get information about cameras pass camera as argument. To get information about deployed models you have to pass model argument like 
```
python  get_va_cloud_data.py camera
```
```
python  get_va_cloud_data.py model
```
### - Camera
###### - In Camera there are four sub arguments
1. -camera_list
2. -camera_info
3. -rtsp
4. -camera_csv
### 1. -camera_list
​
camera_list shows the list of all cameras names
```
python  get_va_cloud_data.py camera -camera_list
```
![Cameras List](images/camera_list.png)
​
### 2. -camera_info
​
This argument take a value as name of the camera and show complete json of that camera. You pass the argument as python  get_va_cloud_data.py camera -camera_info “Developers Space”
​
### Example
```
{'id': 6, 'name': 'Developers Space', 'location': '34.0110647,-118.4107829', 'description': '', 'rtspHost': '10.39.110.246', 'rtspPort': 554, 'rtspPath': '/ch1/main/av_stream.h264', 'rtspUsername': 'dl-team', 'rtspPassword': 'dl@Onstak123', 'image': '6_2.jpg', 'macAddress': None, 'serialKey': None, 'networkId': None, 'ciscoMerakiCameraName': '', 'thermalPort': None, 'createdBy': 'akhter.ali', 'updatedBy': 'amir.nadeem', 'createdAt': '2021-11-01T15:13:43.000Z', 'updatedAt': '2022-09-26T08:32:45.000Z', 'cameraStreamTypeId': 1, 'cameraRTSPInputTypeId': 1, 'make': None, 'model': None, 'accessMethod': None, 'integrationDetailId': None, 'tenantId': 2, 'DLModels': [], 'integration_detail': None}
```
### 3. -rtsp
​
This argument create rtsp of the camera. You to pass camera name as a value
```
python  get_va_cloud_data.py camera -rtsp “Developers Space”
```
### 4. -camera_csv
​
This argument will create and save csv of all the cameras available on the tenant.
```
python get_va_cloud_data.py camera -camera_csv
```
![Cameras info csv](images/cameras_info_csv.png)
​
​
​
​
​
​
​
### Model
​
Get model argument help as 
```
python  get_va_cloud_data.py model --help
```
##### In model there are three sub argument
1. -model_list
2. -mode_info
3. -model_csv
​
### 1. -model_list
​
This will list all the deployed models on the tenant
```
python  get_va_cloud_data.py model -model_list
```
![Models List](images/model_list.png)
​
​
​
​
​
​
### 2. -mode_info
​
This will take model name as value to display complete json of that model.
```
python  get_va_cloud_data.py model -model_info “Occupancy”
```
#### Example
```
​
{'id': 8, 'name': 'Occupancy', 'dlObjects': [{'name': 'Person', 'attributes': [{'key': 'occupancydetected', 'values': ['true', 'false', 'number']}]}], 'description': 'Video analytics occupancy detection', 'image': '1654251858511-792990250.jpg', 'shortDescription': None, 'displayName': 'Occupancy Detection', 'createdAt': '2020-07-01T12:00:00.000Z', 'updatedAt': '2022-06-03T10:24:18.000Z'}
​
```
### 3. -model_csv
​
This argument will create and save csv of all the models available on the tenant.
```
python  get_va_cloud_data.py model -model_csv
```
​
![Model info csv](images/model_info_csv.png)
​
​
​
​
​
​
​
​
# Clone Crowd Repository
```
git clone https://muhammadtalha323@bitbucket.org/muhammadtalha323/crowd.git
```
​
# Envirnment Setup
save the setup.sh and requirements.txt file in the crowd folder
```
bash setup.sh
```
It will create an environment, and install all libraries.
Activate Environment
```
source ~/intr/bin/activate
```
​
# run_new_job.py
this will access new jobs created in the dashboard and save the JSON file in the new_job_run folder. 
```
python run_new_job.py
```
# set_jobs.py
​
this file will get the camera id from JSON in the new_job_run folder. Create workers with camera ids and run every worker. 
```
python set_job.py
```
# server.py
run server.py file. This file takes the images as input and returns the prediction to worker.py.
```
python server.py
```
# woker.py
Set_jobs will automatically run this fill. It takes feed from the camera. pass the input to server.py. takers prediction from server.py. Saves the predicted events image, JSON, and video in a folder "final_videos_images".
# post_job.py
This file will upload the event to the dashboard
```
python post_job.py
```
​
