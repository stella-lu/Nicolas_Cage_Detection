# ObjectDetection
Object detection project for Codeology Fall 2018

This was a 4-week project led by [Micah Harrison](https://github.com/MicahHarrison) to gather data (in this case, images of Nicolas Cage) and use Tensorflow to train a model to detect Nicolas Cage. Jupyter Notebook is used to run the model and show the results and a live webcam stream can be used to detect Nicolas Cage in real time.

For this project, we used a python script to quickly gather 100 - 200 images of our subject from the internet. We then cleaned our data/images and used labelImg to manually label our images and produce accompanying xml files. These xml files contain information about the images' dimensions etc., however the Tensorflow API doesn't use xml files. The xml files were converted to csv files and then to TF records for the Tensorflow API to use. Afterwards, we built our model off of a blank slate object-detection model and began training to minimize loss.


My model has only been trained on 90 images, but it's still not bad! The trained model can be found at:
Nicolas_Cage_Detection/models/research/object_detection/Nicolas

## Setup

	- pip install tensorflow
	- pip install pillow
	- pip install lxml
	- pip install jupyter
	- pip install matplotlib
	- Head to protoc releases page : https://github.com/google/protobuf/releases
	- Download protoc version 3.4.0 for your system and extract it in a folder with ur research models folder
	- Within the research directory, open a terminal and run:
		(C:/Program Files/protoc/bin/protoc) object_detection/protos/*.proto --python_out=.
		(path to protoc.exe)


## Running the Program
	- Navigate to Nicolas_Cage_Detection/models/research/object_detection
	- run "jupyter notebook" and choose Better_Obj_detect_Starter.ipynb
	- Run all cells (either by clicking on the "Run" arrow at the top or by pressing shift+enter)
	- Wait for all cells to finish running (if the [] box looks like [*] then it's still running. If the box has a number in it, it has finished running) and see your results in both images and in the live webcam!

The images that the jupyter notebook runs can be found at:
Nicolas_Cage_Detection/models/research/object_detection/test_images. 

To add or remove images for the model to test, simply add photos here and name them "image[]" where [] is a number in the sequence. Make sure to also change the "range(a, b)" in the line:
TEST_IMAGE_PATHS = [ os.path.join(PATH_TO_TEST_IMAGES_DIR, 'image{}.jpg'.format(i)) for i in range(1, 11) ]
under the "Detection" section in the jupyter notebook to reflect the range of images in the test_images folder (e.g. if we have image1 through to image 10, it should be range(1, 11)).

## Example Screenshots

93% Certainty:

![93% Certainty](/example_screenshots/nicolas_cage_93_percent.png)

91% Certainty:

![91% Certainty](/example_screenshots/nicolas_cage_91_percent.png)

90% Certainty:

![90% Certainty](/example_screenshots/nicolas_cage_90_percent.png)

Example of the live webcam version, with me holding a homemade Nicolas Cage mask (with 83% Certainty):

![webcam](/example_screenshots/nicolas_cage_webcam_83_percent.png)

In comparison, using the live webcam the model believes that I'm Nicolas Cage at 85%, however when testing it out on my friends, the certainty ranged from 60% to 88%. Not bad for only 90 training images.
