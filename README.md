<html>
<head>
</head>
<body>
# Table of Contents
	
[Team Members](#team-members)

[Project Summary](#project-summary)

[Setup](#setup)

[Conclusions](#conclusions)

# <a name="team-members"></a>Team Members
* "TreeMama" <treemamaSEA@gmail.com>


# <a name="project-summary"></a>Project Summary

The purpose of this script is to take RAW files captured by a
[Sony Nex-5 camera](http://www.sansmirror.com/cameras/camera-reviews/sony-nex-camera-reviews/sony-nex-5-review.html "Sony Nex-5 camera") 
(released: May 2010) and generate useful statistics from it. In particular, NDVI and LAI (formulas explained below). The script expects an input of images and 
exports an output folder called 'script_output' of the final results.

The data from the Sony Nex-5 camera used has been hacked to add a [SuperBlue filter](https://www.lifepixel.com/infrared-photography-primer/ch4-internal-filters-for-modified-cameras-super-blue-infrared-filter "SuperBlue filter"). 

**Example without SuperBlue filter:**

![Screenshot](https://raw.github.com/TreeMama/SuperBlue-Calculate-LAI-NDVI/master/Example_NDVI/20130620-152605.JPG)

**Example with SuperBlue filter:**

![Screenshot](https://raw.github.com/TreeMama/SuperBlue-Calculate-LAI-NDVI/master/Example_NDVI/20140620-161402.JPG)

The SuperBlue filter passes blue light AS WELL AS infrared light into the blue channel- thus making it plausible that we could calculate a version of the [NDVI](https://earthobservatory.nasa.gov/features/MeasuringVegetation/measuring_vegetation_2.php "NDVI") using

**This:**

 	- Pixel = (R-B)/(R+B)

**Instead of:**

	- Pixel = (NIR-R)/(NIR+R)

This is an example of an NDVI image calculated using professional Remote Sensing software (which helped correct the white balance issues I was having). My goal was to try to
replicate this result using a different data set and free python libraries.

![Screenshot](https://raw.github.com/TreeMama/SuperBlue-Calculate-LAI-NDVI/master/Example_NDVI/NDVI.jpg)

I also attempted to calculate a version of the [LAI](https://crisp.nus.edu.sg/~acrs2001/pdf/155SAITO.PDF "LAI") using the NDVI I calculated, based on this formula:

	- LAI = 0.57exp(2.33NDVI)

This is an example of a processed result.

![Screenshot](https://raw.github.com/TreeMama/SuperBlue-Calculate-LAI-NDVI/master/Example_NDVI/Capture.PNG)

# <a name="setup"></a>Setup

Python Environment and Libraries are stored in the yaml file.

**You can create needed environment by running the command below in Anaconda:**

	- conda env create --file sony_raw_manipulations.yaml

Or you can import the file in Anaconda Navigator:


Open Navigator -> Environments -> Import -> Select Specification File -> Click "Import"

# <a name="conclusions"></a>Conclusions

It seems very possible to do the math appropriately, but you need to have some decent knowledge about the white balance captured in the image. [Life Pixel's website](https://www.lifepixel.com/infrared-filters-choices/super-blue-infrared-filter "Life Pixel's website")
does a pretty good job showing how the Red channel can be completely oversaturated if your camera is using the AWB. Such an oversaturation in the red channel is going to definitely
cause errors in an NDVI calculation...and there isn't much way to correct that unless you've done some careful light measurements to correct the numbers in post-processing.

That said, since I've been using my kite aerial rig and/or a loaner drone to capture these images, I'm going to have to learn how to do a better white balance estimation on the 
ground (pre-flight ...since I'm obviously not available to set it mid-flight).

..Either way, the code seems sound, and follows the logic and teachings of some of my wise predecessors. For a mere 600 bucks (kite and camera included), I obtained a valuable 
methodology of calculating an individual tree's NDVI and LAI. Considering the thousands usually spent on such an effort - I consider it a win.


**Examples of this being done before:**

Superblue Public Lab:

https://publiclab.org/notes/cfastie/04-20-2013/superblue

Cris Benton calculate NDVI from a Superblue image:

http://research-benton.ced.berkeley.edu/discuss2/index.php?p=/discussion/4813/ir-ndvi-bg3-superblue-oh-my

R studio examples of calculating the NDVI:

https://ourcodingclub.github.io/2019/03/26/spatial.html#section2

https://gist.github.com/nedhorning/f384d9afcc043741def3  

*THIS PROJECT IS COMPLETE AS OF 3/24/2020*
 
</body>
</html>
