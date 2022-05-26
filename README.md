# Thresholding of Images
## Aim
To segment the image using global thresholding, adaptive thresholding and Otsu's thresholding using python and OpenCV.

## Software Required
1. Anaconda - Python 3.7
2. OpenCV

## Algorithm
## Step1:
Load the image and convert the image to Grayscale.

## Step2:
Smoothen the image using Gaussian Method.

## Step3:
Apply thresholding cv2.THRESH_BINARY on the image.

## Step4:
Apply thresholding cv2.THRESH_BINARY_INC on the image.

## Step5:
Apply thresholding cv2.THRESH_TRUNC on the image.

## Step6:
Apply thresholding cv2.THRESH_TOZERO on the image.

## Step7:
Apply thresholding cv2.THRESH_TOZERO_INC on the image.
## Program

```python
Developed By:P.SYAM TEJ
Reg.No:212221240056
import cv2
import matplotlib.pyplot as plt
image = cv2.imread("car.jpg")

# Read the Image and convert to grayscale

grayImage = cv2.cvtColor(image,cv2.COLOR_BGR2GRAY)

# Use Global thresholding to segment the image

ret,thresh = cv2.threshold(grayImage,100,200,cv2.THRESH_BINARY)
ret1,thresh1 = cv2.threshold(grayImage,100,200,cv2.THRESH_BINARY_INV)
ret2, thresh2 = cv2.threshold(grayImage,100,200,cv2.THRESH_TRUNC)
ret3, thresh3 = cv2.threshold(grayImage,100,200,cv2.THRESH_TOZERO)
ret4, thresh4 = cv2.threshold(grayImage,100,200,cv2.THRESH_TOZERO_INV)

# Use Adaptive thresholding to segment the image

th1 = cv2.adaptiveThreshold(grayImage,255,cv2.ADAPTIVE_THRESH_MEAN_C,cv2.THRESH_BINARY,11,2)
th2 = cv2.adaptiveThreshold(grayImage,255,cv2.ADAPTIVE_THRESH_GAUSSIAN_C,cv2.THRESH_BINARY,11,2)
titles = ["Original Image","Adaptive Mean Thresholding","Adaptive Gaussian Thresholding"]
imgs = [grayImage,th1,th2]

# Use Otsu's method to segment the image 
ret5,th3 = cv2.threshold(grayImage,0,255,cv2.THRESH_BINARY+cv2.THRESH_OTSU)

# Display the results

cv2.imshow("Original Image",image)
cv2.imshow("Gray Image",grayImage)
cv2.imshow("THRESH_BINARY",thresh)
cv2.imshow("THRESH_BINARY_INV",thresh1)
cv2.imshow("THRESH_TRUNC",thresh2)
cv2.imshow("THRESH_TOZERO",thresh3)
cv2.imshow("THRESH_TOZERO_INV",thresh4)

for i in range(3):
    plt.subplot(3,1,i+1)
    plt.imshow(imgs[i],'gray')
    plt.title(titles[i])
    plt.xticks([]),plt.yticks([])
plt.show()


cv2.imshow("Otsu method",th3)
cv2.waitKey(0)

```
## Output

### Original Image
![t1](https://user-images.githubusercontent.com/93427224/170474065-8dd77b34-714a-4b00-8b9b-d06802d29706.png)
![t2](https://user-images.githubusercontent.com/93427224/170474098-07747538-85c8-431d-bda3-bd155bb1d26f.png)


### Global Thresholding
![t3](https://user-images.githubusercontent.com/93427224/170474329-017bcffd-d9f0-411c-a2d8-bb44dda106db.png)

![t4](https://user-images.githubusercontent.com/93427224/170474371-afdc329c-db3a-49f3-8809-8eb162aff351.png)

![t5](https://user-images.githubusercontent.com/93427224/170474387-43df37fd-26c5-4bb5-8e09-4bbb7ecda191.png)


### Adaptive Thresholding
![t6](https://user-images.githubusercontent.com/93427224/170474484-3e98f942-708e-4398-b367-b1bfc063e2da.png)


### Optimum Global Thesholding using Otsu's Method

![t7](https://user-images.githubusercontent.com/93427224/170475444-6b17b91e-731d-4854-bcdd-e24cb38183f6.png)


## Result
Thus the images are segmented using global thresholding, adaptive thresholding and optimum global thresholding using python and OpenCV.

