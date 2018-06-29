# GlomPaint 

## HandPicked filter banks (29/June/2018)
Today, two problem was solved(Partly).

First, the wavelength and the standard deviation of the gabor filters are decided.

I use a very simple way to find a good gabor filter bank. I printed all possible combinations of (the wavelength and the standard deviation). The result is [here](https://github.com/ChenxiiGuo/glomDetector/blob/master/developmentLog/images/shortWave.png) and [here](https://github.com/ChenxiiGuo/glomDetector/blob/master/developmentLog/images/longWave.png). 

Finally, the filter bank is like this.

cv2.getGaborKernel((33, 33), 6, np.pi/4, 6, 3, 0, ktype=cv2.CV_32F)
cv2.getGaborKernel((33, 33), 6, np.pi/4, 9, 3, 0, ktype=cv2.CV_32F)
cv2.getGaborKernel((33, 33), 8, np.pi/4, 10, 3, 0, ktype=cv2.CV_32F)
cv2.getGaborKernel((65, 65), 8, np.pi/4, 8, 3, 0, ktype=cv2.CV_32F)

Second, after using filters, there is a problem: How to extract the information from a group of images? 

There are two very straight method do max() or min() in each pixel?

This [image](https://github.com/ChenxiiGuo/glomDetector/blob/master/developmentLog/images/MaxVsMin.png)
shows that min() is better
