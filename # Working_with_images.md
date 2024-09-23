## <center>Working With Images<center>

### Useful Links

[Python Quick Reference](https://www.python.org/ftp/python/doc/1.1/quick-ref.1.1.html)

[Python3 cheat sheet](https://perso.limsi.fr/pointal/_media/python:cours:mementopython3-english.pdf)

[Python.org](https://www.python.org/)

[Python Standard Library](https://docs.python.org/3/library/index.html)

[Python Functions](https://docs.python.org/3/library/functions)

[Python NumPy](https://numpy.org/)

[Matplotlib (PyPlot)](https://matplotlib.org/stable/index.html#)

---

|<td colspan=3> <center><bold><h3>**Table of contents**<center>|||
|---|:---|:---:|
|**01.**|[**Working with Images**](#Working-with-Images;)|RGB colour space<br>set array for image channel<br>Pillow, Image modules<br>open( ), show( ), imshow( ) functions<br> size, format, mode attributes<br> resize an image<br>save image<br>create ndarray from image<br>clipping images<br>broadcasting to an image|

Colour images are represented using the **RGB colour space**. Each colour is represented by a triplet quantifying the amount of red, green, and blue colours. Each colour is represented by an integer number in **`[0, 255]`**   
Some examples:  

* RED: **`[255,0,0]`**  
* GREEN: **`[0,255,0]`**  
* BLUE: **`[0,0,255]`**  
* YELLOW: **`[255,255,0]`**  
* GRAY: **`[100,100,100]`** (by varying the value, you'll get other shades of gray, often defined using **equal values for all three parameters**)
* BLACK: **`[0,0,0]`**   
* WHITE: **`[255,255,255]`**   

If we have an image of size 200x200, we will have a 3D dimensional array (a list containing three tables of size 200x200 &mdash; python won't use this exact representation, but this is a way to see it -- one per each colour).
![RGB Image representation](https://www.researchgate.net/profile/Jane_Courtney2/publication/267210444/figure/fig6/AS:295732335661069@1447519491773/A-three-dimensional-RGB-matrix-Each-layer-of-the-matrix-is-a-two-dimensional-matrix.png)  

**Set array for image channel (gray scale)**:  
**`channelArrayVar = ImageObjVar[:,:,channelIndex]`**  
* Set **`channelIndex`** to the following to set an array for the:  
    * **red channel = 0**  
    * **green channel = 1**  
    * **blue channel = 2**  
    
    * **View with cmap='gray' to get true image**  
* A single channel of an image is known as a gray scale  

**RGBA** color values are an extension of RGB color values with an Alpha channel - which specifies the opacity for a color  
**`rgba(red, green, blue, alpha)`**  
* **`alpha`** is a number between 0.0 (fully transparent) and 1.0 (not transparent at all)  

**Pillow (aka PIL)** module:  

**`!pip install pillow`**  
* Is not built-in, install as shown using **pip**  
* Pillow is a module for processing images in Python  
* It is built on the top of PIL (Python Image Library)  
* Pillow supports many image file formats including BMP, PNG, JPEG, and TIFF  


```python
# Installing pillow module

!pip install pillow
```

    Requirement already satisfied: pillow in c:\users\ajdpi\anaconda3\lib\site-packages (8.4.0)
    

**Import Image module**:  

**`from PIL import Image`**  
* Allows images to be opened and provides functions to load images from files, and to create new images  
* PIL is the Python Imaging Library which provides the python interpreter with image editing capabilities  


```python
# Importing Image module

from PIL import Image
```

**open( )** function:  

**`ImageFileObj = Image.open(imageFilePathAndExtension)`**  
* **pillow provides** the **`open( )`** function read the image  
* A lazy operation; function identifies the file, but the file remains open and the actual image data is not read from the file until you try to process the data (or call the load( ) method)  

**show( )** function:  

**`ImageFileObj.show( )`**  
* **pillow module provides** **`show( )`** function  
* **`show( )`** function displays the image  
* The method is mainly intended for debugging purposes, **better to use matplotlib**    
* On Unix platforms, this method saves the image to a temporary PPM file, and calls the xv utility. On Windows, it saves the image to a temporary BMP file, and **uses** the **standard BMP display utility to show it (usually Paint)**  
* For displaying the image Pillow first converts the image to a .png format (on Windows OS) and stores it in a temporary buffer and then displays it. Therefore, due to the conversion of the image format to .png some properties of the original image file format might be lost (like animation). Therefore, it is advised to use this method only for test purposes  


```python
# opening and showing image (This will display in another program such as paint)

img = Image.open("img/baboon.png")
img.show()
```

Using **pyplot** from **matplotlib**:  

**`from matplotlib import pyplot as plt`**  
**OR**  
**`import matplotlib.pyplot as plt`**  
* Imports **pyplot** sublibrary from matplotlib library  


```python
# Import pyplot

from matplotlib import pyplot as plt
```

**imshow( )** function:  

**`plt.imshow(ImageFileObj, cmap=None)`**  
* **matplotlib** function  
* Used to display data as an image  
* **`ImageFileObj`** is the **data of the image**  
* **`cmap`** is **used** when the **shape** of the array is **2D** (grayscale), but **ignored** when **shape** of the array is **3D**  
[Info on **`imshow`**](https://matplotlib.org/3.5.0/api/_as_gen/matplotlib.pyplot.imshow.html)  
[See for using **`cmap`** parameter - info on matplotlibs colourmap](https://matplotlib.org/stable/tutorials/colors/colormaps.html)  
[More info on cmap](https://stackoverflow.com/questions/25625952/matplotlib-what-is-the-function-of-cmap-in-imshow)


```python
# Show image

plt.imshow(img)
```




    <matplotlib.image.AxesImage at 0x223a779b460>




    
![png](%23%20Working_with_images_files/%23%20Working_with_images_22_1.png)
    


**size** attribute:  

**`ImageFileObj.size`**  
* Provides the size of the image returned as a **tuple** that contains **width** and **height**  
* Part of **Image class**  


```python
# Getting size of image

img.size
```




    (512, 512)



**format** attribute:  

**`ImageFileObj.format`**  
* Returns the **format** of the image file  
* Part of **Image class**  


```python
# Getting format of image

img.format
```




    'PNG'



**mode** attribute:  

**`ImageFileObj.mode`**  
* Part of **Image class**  
* Tells the type and depth of the pixel in the image  
* A 1-bit pixel has a range of 0-1, and an 8-bit pixel has a range of 0-255  
* There are different modes provided by this module. A few of them are:

|**Mode**|**Description**|
|:---|:---|
|1|1-bit pixels, black and white|
|L|8-bit pixels, Greyscale|
|P|8-bit pixels, mapped to any other mode using a color palette|
|RGB|3×8-bit pixels, true color|
|RGBA|4×8-bit pixels, true color with transparency mask|


```python
# Getting mode of image

img.mode
```




    'RGB'



**Resize an image**:  

**`rescaledVar = ImageFileObj.resize(newSize)`**  
* **`newSize`** should be passed as a **tuple**  
* Part of **Image class**  


```python
resizedImg = img.resize((128,128))
plt.imshow(resizedImg)
```




    <matplotlib.image.AxesImage at 0x223a7ee07f0>




    
![png](%23%20Working_with_images_files/%23%20Working_with_images_30_1.png)
    


**Save image**:  

**`PIL_imageObj.save(filePathWithExtension, imageType)`**  
* Part of **Image class**  
* Saves an image that has been previously loaded - easier as **PIL image object** than image file object  
* Note you can save an image as a different **`imageType`** than the original was opened as  


```python
# Saving resized image as a jpeg (original was png)

resizedImg.save("data/ResizedBaboon.jpeg", "jpeg")
```

**Create ndarray from an image**:  

**`imgArrayVar = np.asarray(ImageFileObj)`**  
* Creates a numpy array from an Image file object  
* Images will be a 3D array  


```python
# Casting an Image file object to a ndarray

import numpy as np

imgArray = np.asarray(img)

print(imgArray.shape)
print(imgArray)
```

    (512, 512, 3)
    [[[164 150  71]
      [ 63  57  31]
      [ 75  43  10]
      ...
      [117 119  68]
      [141 170 101]
      [179 188 118]]
    
     [[120 125  62]
      [135  97  33]
      [ 55  35  23]
      ...
      [122 140  98]
      [136 159 128]
      [120 138  74]]
    
     [[ 99  74  31]
      [132 118  46]
      [ 60  41  36]
      ...
      [118  93  90]
      [ 87  91  77]
      [ 96  80  49]]
    
     ...
    
     [[121 148 155]
      [123 156 150]
      [124 150 139]
      ...
      [110  73  60]
      [ 90  93  70]
      [ 81  80  60]]
    
     [[126 169 168]
      [117 151 151]
      [121 136 133]
      ...
      [ 73  84  68]
      [ 99  69  86]
      [ 80  63  71]]
    
     [[  9  11  12]
      [ 10  12  11]
      [ 11  15  12]
      ...
      [  5   8   5]
      [  2   5   0]
      [  4   5   2]]]
    

**Clipping images**:  

**`newArrayVar = ndarrayVar/255`**$\;\;\;\;$**(or other mathematical operation)**  
* By using **mathematical operators**, we can adjust the values in an **array for an image**  
* **matplotlib (plt)** is able to show images represented as **floats** in the range **[0..1]** and **integers** in the range **[0..255]**  
* Values **below 0 are considered as 0**, values **above 1 are considered as 1**  for **floats**, **same applies** when outside **integer range**  


```python
# Clipping an image array so values are between 0 and 1 (original values were 0-255, so dividing by 255)

clippedImgArray = imgArray/255

plt.imshow(clippedImgArray)
```




    <matplotlib.image.AxesImage at 0x223a8561ca0>




    
![png](%23%20Working_with_images_files/%23%20Working_with_images_36_1.png)
    



```python
clippedImgArray
```




    array([[[0.64313725, 0.58823529, 0.27843137],
            [0.24705882, 0.22352941, 0.12156863],
            [0.29411765, 0.16862745, 0.03921569],
            ...,
            [0.45882353, 0.46666667, 0.26666667],
            [0.55294118, 0.66666667, 0.39607843],
            [0.70196078, 0.7372549 , 0.4627451 ]],
    
           [[0.47058824, 0.49019608, 0.24313725],
            [0.52941176, 0.38039216, 0.12941176],
            [0.21568627, 0.1372549 , 0.09019608],
            ...,
            [0.47843137, 0.54901961, 0.38431373],
            [0.53333333, 0.62352941, 0.50196078],
            [0.47058824, 0.54117647, 0.29019608]],
    
           [[0.38823529, 0.29019608, 0.12156863],
            [0.51764706, 0.4627451 , 0.18039216],
            [0.23529412, 0.16078431, 0.14117647],
            ...,
            [0.4627451 , 0.36470588, 0.35294118],
            [0.34117647, 0.35686275, 0.30196078],
            [0.37647059, 0.31372549, 0.19215686]],
    
           ...,
    
           [[0.4745098 , 0.58039216, 0.60784314],
            [0.48235294, 0.61176471, 0.58823529],
            [0.48627451, 0.58823529, 0.54509804],
            ...,
            [0.43137255, 0.28627451, 0.23529412],
            [0.35294118, 0.36470588, 0.2745098 ],
            [0.31764706, 0.31372549, 0.23529412]],
    
           [[0.49411765, 0.6627451 , 0.65882353],
            [0.45882353, 0.59215686, 0.59215686],
            [0.4745098 , 0.53333333, 0.52156863],
            ...,
            [0.28627451, 0.32941176, 0.26666667],
            [0.38823529, 0.27058824, 0.3372549 ],
            [0.31372549, 0.24705882, 0.27843137]],
    
           [[0.03529412, 0.04313725, 0.04705882],
            [0.03921569, 0.04705882, 0.04313725],
            [0.04313725, 0.05882353, 0.04705882],
            ...,
            [0.01960784, 0.03137255, 0.01960784],
            [0.00784314, 0.01960784, 0.        ],
            [0.01568627, 0.01960784, 0.00784314]]])




```python
# Further reducing the array range of values changes the appearence
# 1st clipped image, values ranged 0-1, dividing by 2 they now range 0-0.5 essentially darkening the image

clippedImgArrayHalf = clippedImgArray/2

plt.imshow(clippedImgArrayHalf)
```




    <matplotlib.image.AxesImage at 0x223a8bd3dc0>




    
![png](%23%20Working_with_images_files/%23%20Working_with_images_38_1.png)
    



```python
clippedImgArrayHalf
```




    array([[[0.32156863, 0.29411765, 0.13921569],
            [0.12352941, 0.11176471, 0.06078431],
            [0.14705882, 0.08431373, 0.01960784],
            ...,
            [0.22941176, 0.23333333, 0.13333333],
            [0.27647059, 0.33333333, 0.19803922],
            [0.35098039, 0.36862745, 0.23137255]],
    
           [[0.23529412, 0.24509804, 0.12156863],
            [0.26470588, 0.19019608, 0.06470588],
            [0.10784314, 0.06862745, 0.04509804],
            ...,
            [0.23921569, 0.2745098 , 0.19215686],
            [0.26666667, 0.31176471, 0.25098039],
            [0.23529412, 0.27058824, 0.14509804]],
    
           [[0.19411765, 0.14509804, 0.06078431],
            [0.25882353, 0.23137255, 0.09019608],
            [0.11764706, 0.08039216, 0.07058824],
            ...,
            [0.23137255, 0.18235294, 0.17647059],
            [0.17058824, 0.17843137, 0.15098039],
            [0.18823529, 0.15686275, 0.09607843]],
    
           ...,
    
           [[0.2372549 , 0.29019608, 0.30392157],
            [0.24117647, 0.30588235, 0.29411765],
            [0.24313725, 0.29411765, 0.27254902],
            ...,
            [0.21568627, 0.14313725, 0.11764706],
            [0.17647059, 0.18235294, 0.1372549 ],
            [0.15882353, 0.15686275, 0.11764706]],
    
           [[0.24705882, 0.33137255, 0.32941176],
            [0.22941176, 0.29607843, 0.29607843],
            [0.2372549 , 0.26666667, 0.26078431],
            ...,
            [0.14313725, 0.16470588, 0.13333333],
            [0.19411765, 0.13529412, 0.16862745],
            [0.15686275, 0.12352941, 0.13921569]],
    
           [[0.01764706, 0.02156863, 0.02352941],
            [0.01960784, 0.02352941, 0.02156863],
            [0.02156863, 0.02941176, 0.02352941],
            ...,
            [0.00980392, 0.01568627, 0.00980392],
            [0.00392157, 0.00980392, 0.        ],
            [0.00784314, 0.00980392, 0.00392157]]])




```python

```


```python
# clippedImgArray values ranged 0-1
# Multiplying them by 2 gives values in the range 0-2
# Because it contains floats, when using matplotlib, anything above 1 is assumed to be 1
# This changes the appearence of the image

clippedImgBreachingFloatRange = clippedImgArray*2

plt.imshow(clippedImgBreachingFloatRange)
```

    Clipping input data to the valid range for imshow with RGB data ([0..1] for floats or [0..255] for integers).
    




    <matplotlib.image.AxesImage at 0x223a9e70820>




    
![png](%23%20Working_with_images_files/%23%20Working_with_images_41_2.png)
    



```python
clippedImgBreachingFloatRange
```




    array([[[1.28627451, 1.17647059, 0.55686275],
            [0.49411765, 0.44705882, 0.24313725],
            [0.58823529, 0.3372549 , 0.07843137],
            ...,
            [0.91764706, 0.93333333, 0.53333333],
            [1.10588235, 1.33333333, 0.79215686],
            [1.40392157, 1.4745098 , 0.9254902 ]],
    
           [[0.94117647, 0.98039216, 0.48627451],
            [1.05882353, 0.76078431, 0.25882353],
            [0.43137255, 0.2745098 , 0.18039216],
            ...,
            [0.95686275, 1.09803922, 0.76862745],
            [1.06666667, 1.24705882, 1.00392157],
            [0.94117647, 1.08235294, 0.58039216]],
    
           [[0.77647059, 0.58039216, 0.24313725],
            [1.03529412, 0.9254902 , 0.36078431],
            [0.47058824, 0.32156863, 0.28235294],
            ...,
            [0.9254902 , 0.72941176, 0.70588235],
            [0.68235294, 0.71372549, 0.60392157],
            [0.75294118, 0.62745098, 0.38431373]],
    
           ...,
    
           [[0.94901961, 1.16078431, 1.21568627],
            [0.96470588, 1.22352941, 1.17647059],
            [0.97254902, 1.17647059, 1.09019608],
            ...,
            [0.8627451 , 0.57254902, 0.47058824],
            [0.70588235, 0.72941176, 0.54901961],
            [0.63529412, 0.62745098, 0.47058824]],
    
           [[0.98823529, 1.3254902 , 1.31764706],
            [0.91764706, 1.18431373, 1.18431373],
            [0.94901961, 1.06666667, 1.04313725],
            ...,
            [0.57254902, 0.65882353, 0.53333333],
            [0.77647059, 0.54117647, 0.6745098 ],
            [0.62745098, 0.49411765, 0.55686275]],
    
           [[0.07058824, 0.08627451, 0.09411765],
            [0.07843137, 0.09411765, 0.08627451],
            [0.08627451, 0.11764706, 0.09411765],
            ...,
            [0.03921569, 0.0627451 , 0.03921569],
            [0.01568627, 0.03921569, 0.        ],
            [0.03137255, 0.03921569, 0.01568627]]])



**Broadcasting to an image**:  

**`newImgVar = clippedImageVar*broadcastArray`**  
* **`clippedImageVar`** should be **clipped** to keep any **scaled values** inside the **image range** for floats (0-1)  
* **`broadcastArray`** should be **same shape** as image  
* Sometimes you may need to add an axis to an array to make it the same shape (see Numpy)  


```python
# Creates a 2D array of zeros 
# 512x512 (same dimentions as each RGB channel in standard medium sized image)

array = np.zeros((512,512))

print(array)
plt.imshow(array, cmap='gray')
```

    [[0. 0. 0. ... 0. 0. 0.]
     [0. 0. 0. ... 0. 0. 0.]
     [0. 0. 0. ... 0. 0. 0.]
     ...
     [0. 0. 0. ... 0. 0. 0.]
     [0. 0. 0. ... 0. 0. 0.]
     [0. 0. 0. ... 0. 0. 0.]]
    




    <matplotlib.image.AxesImage at 0x223aa0f0160>




    
![png](%23%20Working_with_images_files/%23%20Working_with_images_44_2.png)
    



```python
# Can set segments of the array to create a pattern

array[:256,256:] = 0.5     # top right segment
array[256:,:256] = 1       # bottom left segment
array[:256,:256] = 0.75    # top left segment
print(array.shape)
plt.imshow(array, cmap="gray")      # maps array to all 3 RGB channels
```

    (512, 512)
    




    <matplotlib.image.AxesImage at 0x223aa1011c0>




    
![png](%23%20Working_with_images_files/%23%20Working_with_images_45_2.png)
    



```python
array
```




    array([[0.75, 0.75, 0.75, ..., 0.5 , 0.5 , 0.5 ],
           [0.75, 0.75, 0.75, ..., 0.5 , 0.5 , 0.5 ],
           [0.75, 0.75, 0.75, ..., 0.5 , 0.5 , 0.5 ],
           ...,
           [1.  , 1.  , 1.  , ..., 0.  , 0.  , 0.  ],
           [1.  , 1.  , 1.  , ..., 0.  , 0.  , 0.  ],
           [1.  , 1.  , 1.  , ..., 0.  , 0.  , 0.  ]])




```python
# Adds new axis to 2D array to create 3D array to broadcast to image

array2 = array[:,:,np.newaxis]

newImg = clippedImgArray*array2    # Broadcasts 3D array to image

plt.imshow(newImg)
```




    <matplotlib.image.AxesImage at 0x223aa3c3d30>




    
![png](%23%20Working_with_images_files/%23%20Working_with_images_47_1.png)
    


[<p style="text-align: right;">**⬆ Top of Page ⬆**</p>](#Working-With-Images)

---
