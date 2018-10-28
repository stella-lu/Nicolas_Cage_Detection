# ObjectDetection
Object detection project for Codeology Fall 2018

This was a 4-week project led by Micah Harrison to gather data (images of Nicolas Cage) and use Tensorflow to train a model to detect Nicolas Cage. Jupyter Notebook is used to run the model and show the results and a live webcam stream can be used to detect Nicolas Cage in real time.

## SETUP

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

The images that the jupyter notebook runs can be found at Nicolas_Cage_Detection/models/research/object_detection/test_images. To add or remove images for the model to test, simply add photos here and name them "image[]" where [] is a number in the sequence. Make sure to also change the "range(a, b)" in the line:
TEST_IMAGE_PATHS = [ os.path.join(PATH_TO_TEST_IMAGES_DIR, 'image{}.jpg'.format(i)) for i in range(1, 11) ]
under the "Detection" section in the jupyter notebook to reflect the range of images in the test_images folder (e.g. if we have image1 through to image 10, it should be range(1, 11)).
