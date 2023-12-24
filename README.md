# Openinapp-Assignment-3
Showcase your proficiency in developing an advanced AI model capable of enhancing the quality of a video by upscaling its resolution and reducing noise. And only use the videos provided in the PDF to work on the upscaling task.
Real-ESRGAN Video Enhancement
This guide outlines the steps to enhance a video using Real-ESRGAN, a Super-Resolution Generative Adversarial Network (SRGAN) for image and video enhancement.

Step 1: Download Required Libraries
Clone the Real-ESRGAN repository.
Navigate to the Real-ESRGAN directory.
Install necessary Python libraries using the following commands:
bash
Copy code
pip install basicsr facexlib gfpgan
pip install -r requirements.txt
python setup.py develop
Download the pre-trained model:
bash
Copy code
wget https://github.com/xinntao/Real-ESRGAN/releases/download/v0.1.0/RealESRGAN_x4plus.pth -P experiments/pretrained_models
Step 2: Upload the Video File
If Google Drive is not mounted:
Create an "upload" folder if it doesn't exist.
Upload the video file to the "upload" folder.
Step 3: Extract Frames from the Video
If the "tmp_frames" folder exists, remove its contents.
Create the "tmp_frames" folder.
Extract frames from the uploaded video using FFmpeg.
Step 4: Run Real-ESRGAN on Extracted Frames
Navigate to the Real-ESRGAN directory.
Run the Real-ESRGAN inference script:
bash
Copy code
python inference_realesrgan.py -n RealESRGAN_x4plus -i ../tmp_frames --outscale 4 --face_enhance
Step 5: Create the Enhanced Video
If the "results" folder exists, remove its contents.
Create the "results" folder.
Recompile the enhanced frames into a video using FFmpeg:
bash
Copy code
ffmpeg -i /content/Real-ESRGAN/results/frame_%08d_out.png -c:a copy -c:v libx264 -r 15 -pix_fmt yuv420p results/enhanced_{file_name}
Final Result:
The enhanced video is saved in the path: /content/Real-ESRGAN/results.
