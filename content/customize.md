# Customizing walle-ng

All settings for walle-ng are set in the ```config.cfg``` file located in the config directory. A more detailed explanation of the parameters are as follows:

```bash
[General]
# Input video device, default is 0
input_video    =0

# Output steam file. This writes the video stream to /tmp and can be read by other applications
output_video   =/tmp/output.mpeg

# Show the video stream in a seperate window on the desktop. Set to False for headless installs.
do_output      =True

# Auto-pause after each frame
do_timelapse   =False

# Crop the input stream to this width
crop_width     =0

# Crop the input stream to this height
crop_height    =0

# Output log file for debugging
log_file       =/home/pi/Walle-ng/walle-ng.log

[Faces]
# Path to headshots for performing face identification
# Images should be in the format of Name-0.jpg, Name-1.png
db_path        =/home/pi/Walle-ng/dataset

# Use Face Detection model to find faces on the face images, otherwise use full images.
do_detector    =False

[Model]
# Face detection model path
model_fd      =/home/pi/Walle-ng/models/face-detection-retail-0005.xml

# Landmark regression model path
model_ld      =/home/pi/Walle-ng/models/landmarks-regression-retail-0009.xml

# Face reidentification model path
model_rd      =/home/pi/Walle-ng/models/face-reidentification-retail-0095.xml

[Inference]
# Inference device, can be [CPU,GPU,FPGA,MYRIAD,HETERO]
# To use Movidius, set to MYRIAD
device_fd      =MYRIAD
device_lm      =MYRIAD
device_rd      =MYRIAD

# Probability threshold for face detections
thresh_fd      =0.6

# Cosine distance threshold between two vectors for face identification
thresh_rd      =0.3

# Scaling ratio for bboxes passed to face recognition
scale_ratio    =1.15

# Show verbose debugging to logs
do_verbose     =False

# Show stats
do_stats       =False

# Allow growing the face database, in addition allow dumping new faces on disk. In that
# case the user will be asked if he wants to add a specific image to the images gallery.
# The user should specify the name for the image in the open window and press `Enter`.
# If it's not, then press `Escape`. The user may add new images for the same person by 
# setting the same name in the open window.
do_grow        =False

[AWS]
# AWS API Gateway endpoint URL. This should point to the POST request URL
notify_url     =<api_gateway_endpoint_url>

# AWS API Gateway API Key
api_key	       =<api_gateway_api_key>

# Enable/Disable notifications, True = Enabled
do_notify      =True

```