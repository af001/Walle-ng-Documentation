# Install walle-ng on Raspberry Pi

In a shell, clone the Walle-ng project to the Pi using ```git```. If this is intended to be set up as a headless install, meaning Walle-ng will start on boot using the provided systemd service, it is recommended to add custom head shots of known users prior to running ```./install.sh```. If this is a normal install where the camera output will be viewed by directly running ```python3 walle-ng.py```, the images can be added after running the install script when the device reboots. In the event there are download errors when running the install script, it may be necessary to modify the install script to point to the latest download URLs to fix the broken links.

When running ```./install.sh```, a series of questions will be presented based on how the user intends on running walle-ng. The first question asks if this will be run in headless mode. By saying 'y' to this, it modifies the ```config.cfg``` file so that the video stream is not output to the Desktop. The following question to this is do you want to create a systemd service to start walle-ng on boot. If this is also set to 'y', then a file called ```walled.service``` will be placed in /etc/systemd/system and enabled to start ```walle-ng.py``` on boot.

The next set of questions asks the user if they intend on setting up notifications using AWS. If the user says 'y' to this, the first question asks the user to input the endpoint URL. This is the URL that was saved earlier when setting up API Gateway, and for this example was ```https://2szxrk2gh4.execute-api.us-east-1.amazonaws.com/prod/walle-ng-api```. The next question asks the user to enter their API Gateway API key. 

```bash
# In the pi user context, clone the project to the Pi user's root directory
cd ~/
git clone https://github.com/af001/Walle-ng.git
chmod 755 install.sh
./install.sh
```