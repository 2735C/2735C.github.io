---
title: "Example Post: thumbnail exists"
date: "2023-12-02"
thumbnail: "/assets/img/thumbnail/bricks.webp"
---

# Follow the guidance
---

**Fill the image path to the 'thumbnail' attribute, if you want a main image to be displayed on the post header image.**

```
---
title: "Example Post: thumbnail exists"
date: "2023-12-02"
thumbnail: "/assets/img/thumbnail/bricks.webp"
---
```

##  IMAGE - Basic Operation

* Terminal

```
#VS code 파일 생성
code opencv_1.py

# 실행
python opencv_1.py
```

* image를 read /write /display

![Image](https://github.com/user-attachments/assets/9490f7eb-e05f-4870-bce6-1223e2ae9887)|
--|

![Image](https://github.com/user-attachments/assets/da94dac2-a0f1-40d7-96df-6c9fd35a9bfe)|
--|


```python
import cv2
import numpy as np


# Read image file
img = cv2.imread("my_input.jpg")

# Make Display channel as name of Image
cv2.namedWindow("image", cv2.WINDOW_NORMAL)

# Numpy ndarray H/W/C order
print(img.shape)

# Display Image file which is Read
cv2.imshow("image", img)

# Wait before any key import
cv2.waitKey(0)

# Save Read Image file as output.png
cv2.imwrite("output.png", img)

# Destroy all windows
cv2.destroyAllWindows()

```

* RGB/HSV 

![Image](https://github.com/user-attachments/assets/fe309de7-12c3-4023-9eb6-198d8c3ae8f2)|
--|


![Image](https://github.com/user-attachments/assets/899a7291-270b-4b97-879d-d446483af129)|
--|

![Image](https://github.com/user-attachments/assets/48eb279f-e09c-4ee3-b6ca-a59e7d1cdbdc)|
--|
![Image](https://github.com/user-attachments/assets/57927f8e-a356-41c0-925e-125a82a7d549)|

```python
import numpy as np
import cv2

#이미지 파일을 Read하고 Color space 정보 출력
color = cv2.imread("PINK.jpg", cv2.IMREAD_COLOR)
#color = cv2.imread("strawberry_dark.jpg", cv2.IMREAD_COLOR)
print(color.shape)

height,width,channels =  color.shape
resized = cv2.resize(color, (800,1200))

cv2.imshow("Original Image", resized)

# Wait before any key import
cv2.waitKey(0)

#Color Channel 을 B,G,R로 분할하여 출려
b,g,r = cv2.split(resized)
rgb_split = np.concatenate((b,g,r),axis = 1)
cv2.imshow("BGR Channels", rgb_split)

# Wait before any key import
cv2.waitKey(0)

#색공간을 BGR에서 HSV로 변환
hsv = cv2.cvtColor(resized, cv2.COLOR_BGR2HSV)

# Wait before any key import
cv2.waitKey(0)

#Channel을 H,S,V로 분할하여 출력
h,s,v = cv2.split(hsv)
hsv_split = np.concatenate((h,s,v),axis = 1)
cv2.imshow("Split HSV", hsv_split)


# Wait before any key import
cv2.waitKey(0)

# Destroy all windows
cv2.destroyAllWindows()
```

* **Crop / Resize** 

![Image](https://github.com/user-attachments/assets/ec0ed2dd-fd05-4ef3-8be7-4ec6e3a44e4a)|
--|

![Image](https://github.com/user-attachments/assets/f4a3fe0f-1bff-4389-9bfe-3bf2f76d88f8)|
--|

```python
import cv2
import numpy as np

#이미지 파일을 Read

img = cv2.imread("my_input.jpg")

#Crop 300x400 from original image from (100, 50) = (x, y)
cropped = img[600:1100, 500:900]

#Resize cropped image from 300x400 to 400x200
resized = cv2.resize(cropped, (300,400))

#Display all
cv2.imshow("original", img)
cv2. waitKey(0)

cv2.imshow("Cropped image", cropped)
cv2. waitKey(0)

cv2.imshow("Resuzed image", resized)
cv2. waitKey(0)
cv2.destroyAllWindows
```

* **Rotate**

![Image](https://github.com/user-attachments/assets/5b0f43ac-eec7-4ee6-b9a8-81dab6782331)|
--|

```python
import numpy as np
import cv2

#이미지 파일을 Read하고 Color space 정보 출력
color = cv2.imread("Rotate.jpg", cv2.IMREAD_COLOR)

resized1 = cv2.resize(color, (800,1000))
resized2= cv2.resize(color, (400,500))
rotated = cv2.rotate(resized2,cv2.ROTATE_90_CLOCKWISE)

cv2.imshow("Original Image", resized1)
cv2.waitKey(0)

cv2.imshow("Rotated image", rotated)
cv2.waitKey(0)
cv2.destroyAllWindows()
```