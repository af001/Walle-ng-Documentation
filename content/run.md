# Running walle-ng on Raspberry Pi

Before running the application, users must place images in the ```dataset``` directory. It is recommended to place 1-10 images for each user in the dataset directory. Images should be cropped to only include the heads of users, and each image should be labeled sequentially. An example of this would be Anton-0.jpg, Anton-1.jpg, Jane-0.png, Jane-1.png, etc. The Python script that reads the files expects the format to be either .jpg or .png, and the name associated with the photos will be the name used when sending notifications. The Raspberry Pi can be used to take photos. For users that would like to use the Raspberry Pi cam, issue the following command in a terminal:

```bash
raspistill -o Anton-0.jpg
raspistill -o Anton-1.jpg
```

For headless installs that implement systemd, apply power and the walle-ng device should automatically start tracking faces and sending notifications. Things to consider if using headless are 1) make sure to have your images set in the ```dataset``` directory and 2) to validate the device is running ssh to the Pi and run ```sudo systemctl status walled```. To start and stop the service, issue ```sudo systemctl stop walled``` or ```sudo systemctl start walled```.

For installations that intend on using the Desktop GUI, then starting the application can be done by opening a terminal and executing ```cd Walle-ng && python3 wally-ng.py```. To quit running the application, place focus on the window that contains the video and press the ```q``` button. Things to consider are 1) make sure to have your images set in the ```dataset``` directory and 2) you must login to the Pi Desktop in order to view the output of the video stream. 

```bash
# Open a terminal on the Pi Desktop
cd ~/Walle-ng
python3 walle-ng.py
```

As an alternative to logging into the Pi desktop, you can use SSH on your host computer and run the following commands to view stream:

```bash
# SSH to the Pi with the -X option to view the steam on your host machine
ssh -X pi@192.168.198.167
cd ~/Walle-ng
python3 walle-ng.py
```
