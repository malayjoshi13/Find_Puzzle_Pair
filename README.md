# Find_Puzzle_Pair

Find_Puzzle_Pair is **Computer vision** and **Deep learning** based **pair finder** which by using **Siamese neural network** find partner of a given puzzle piece that could fit with it.

Unlike a conventional CNN, the Siamese Network does not classify the images into certain categories or labels, rather it only finds out the distance between any two given images. If the images have the same label, then the network should learn the parameters, i.e. the weights and the biases in such a way that it should produce a smaller distance between the two images, and if they belong to different labels, then the distance should be larger.

As an example, for such given input image of a puzzle piece,

![bandicam 2021-12-27 00-00-23-384](https://user-images.githubusercontent.com/71775151/147417044-3feab6bb-ced2-4a90-87f8-438d4aed337e.jpg)

we want to find such like puzzle piece so that both could form a pair which fits into each other.

![bandicam 2021-12-27 00-00-52-038](https://user-images.githubusercontent.com/71775151/147417046-867b3c23-53f3-4b90-93c8-1e1ceb8ba6de.jpg)

## What makes Find_Puzzle_Pair work?
The basic principle on which it works is that if done thresholding of pair images in complimentary/opposite manners then they both will look much similar to each other. This means if we do **THRESH_BINARY** thresholding of first puzzle piece to make it look like from this 

![bandicam 2021-12-27 00-00-23-384](https://user-images.githubusercontent.com/71775151/147417044-3feab6bb-ced2-4a90-87f8-438d4aed337e.jpg)

to this.

![bandicam 2021-12-27 00-28-56-195](https://user-images.githubusercontent.com/71775151/147417572-dccfd9ef-d3d3-421c-bc86-c349751b495b.jpg)

And do **THRESH_BINARY_INV** thresholding with another piece to make it look like from this

![bandicam 2021-12-27 00-00-52-038](https://user-images.githubusercontent.com/71775151/147417046-867b3c23-53f3-4b90-93c8-1e1ceb8ba6de.jpg)

to this.

![bandicam 2021-12-27 00-29-25-821](https://user-images.githubusercontent.com/71775151/147417579-ee3bb1c2-6d8f-4e1d-b330-e7beae6bcc4e.jpg)

Then we could say that both threholded images look much similar.

Thus after making all training pairs given in ```training_data.csv```file in such complimentary thresholded format, we train Siamese model by help of ```similarity2.ipynb``` file (link:- https://colab.research.google.com/drive/1y01t-6FmIvilFsKIqnAdhE_HXkq_CnIs?usp=sharing) to understand how a particular pair look similar to each other and how much different from any randomly taken puzzle piece. 

After training is over the trained model will find puzzle pairs that when complimentary thresholded looks similar. These pairs are actually the same pairs that we are looking for which will fit together in each other.   

## Usage
Users can go through the whole training process from this file (https://colab.research.google.com/drive/1y01t-6FmIvilFsKIqnAdhE_HXkq_CnIs?usp=sharing). Dataset can be found here https://drive.google.com/drive/folders/1x0HgL6yH7URfFD68LhXBErf3KhzdsydN?usp=sharing. 
