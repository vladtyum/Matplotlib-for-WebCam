# Matplotlib-for-WebCam

purpose of this rep is to fill gaps of getting info from WebCam

two issues are seen so far

1. Bad understanding of MPL terminology
2. MPL animation
3. Integration with videostream

Starting with going through MPL tutorials

[usage_faq.html#parts-of-a-figure](https://matplotlib.org/faq/usage_faq.html#parts-of-a-figure)  
too dense than i need

thats' what i need
```python
import matplotlib.pyplot as plt
plt.plot([1, 2, 3, 4], [1, 4, 9, 16])
plt.show()
```
so that thing just gives coordinates, MPL then plotting it itself

cool cool

axis' sizes

```python
plt.axis([0, 6, 0, 20])
```
This code works with numpy, very good simplest example
```python
import numpy as np

# evenly sampled time at 200ms intervals
t = np.arange(0., 5., 0.2)

# red dashes, blue squares and green triangles
plt.plot(t, t, 'r--', t, t**2, 'bs', t, t**3, 'g^')
plt.show()
```

which shows plt.plot() can plot several datasets at the same time

> ```python
>and gcf() returns the current figure  
>```
this what i was confused about

 Great thing would be to jump from here up to animation

 ```python
#SIMPLIEST WORKING VERSION
 import cv2
 import numpy as np
 from matplotlib import pyplot as plt

 cap = cv2.VideoCapture(0)
 while(True):
 	ret,frame = cap.read()
 	hist = cv2.calcHist([frame],[0],None,[256],[0,256])
 	plt.plot(hist)
 	plt.show()

 ```
this code takes input, now let's animate it



Done
```python
import cv2
import numpy as np
from matplotlib import pyplot as plt
from matplotlib.animation import FuncAnimation

cap = cv2.VideoCapture(0)

def update(i):
	ret,frame = cap.read()
	hist = cv2.calcHist([frame],[0],None,[256],[0,256])
	plt.cla()
	plt.plot(hist)


ani = FuncAnimation(plt.gcf(), update, interval=200)
plt.show()
```
