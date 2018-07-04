# GlomPaint 

## HandPicked filter banks (29/June/2018)
Today, two problem was solved(Partly).

First, the wavelength and the standard deviation of the gabor filters are decided.

I use a very simple way to find a good gabor filter bank. I printed all possible combinations of (the wavelength and the standard deviation). There two images shows the result of these combinations.
![image](https://github.com/ChenxiiGuo/glomDetector/blob/master/developmentLog/images/shortWave.png) 
![image](https://github.com/ChenxiiGuo/glomDetector/blob/master/developmentLog/images/longWave.png). 

Finally, the filter bank is like this.

cv2.getGaborKernel((33, 33), 6, np.pi/4, 6, 3, 0, ktype=cv2.CV_32F)

cv2.getGaborKernel((33, 33), 6, np.pi/4, 9, 3, 0, ktype=cv2.CV_32F)

cv2.getGaborKernel((33, 33), 8, np.pi/4, 10, 3, 0, ktype=cv2.CV_32F)

cv2.getGaborKernel((65, 65), 8, np.pi/4, 8, 3, 0, ktype=cv2.CV_32F)

Second, after using filters, there is a problem: How to extract the information from a group of images? 

There are two very straight method do max() or min() in each pixel?

This [image](https://github.com/ChenxiiGuo/glomDetector/blob/master/developmentLog/images/MaxVsMin.png)
shows that min() is better

## Finished the development by using gabor filters(3/July/2018)

The gabor filters combine with KNN works well.

This image shows the results for a high quality image. It works well.
![image](https://github.com/ChenxiiGuo/glomDetector/blob/master/segment/report/pureBackground.png)
However, there are still some problems. 

Firstly, some cells are in the needle and it should not be counted as glomeruli which is required by Bristol Renal Team. However, using gabor cannot avoid this due to the fact that the texture of these cells are similar to the glomeruli part.

Secondly, if the background is not pure, then the result is not good. This image shows when the background is not pure, the false postive problem is serious. However, in pratical jobs, this is not a serious problem since researchers in Bristol Renal Team can avoid these videos. 
![image](https://github.com/ChenxiiGuo/glomDetector/blob/master/segment/report/blurBackground.png)
