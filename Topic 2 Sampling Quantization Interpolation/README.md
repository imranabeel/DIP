# Sampling, Quantization and Interpolation

## 1D interpolation
Use any of the following command to install "scipy" library if you get an error. 

 > sudo pip install scipy
or 
> sudo pip3 install scipy
or 
> conda install scipy
```python

from scipy import power, arange
from scipy.interpolate import interp1d
x = arange(0, 5)
y = power(x + 2, 3)
xnew = arange(0, 4, 0.5)

f = interp1d(x, y)
print f(xnew)

OUTPUT
[   8.    17.5   27.    45.5   64.    94.5  125.   170.5]

f = interp1d(x, y, "zero")
print f(xnew)

OUTPUT
[   8.    8.   27.   27.   64.   64.  125.  125.]

f = interp1d(x, y, "cubic")
print f(xnew)

OUTPUT
[   8.      15.625   27.      42.875   64.      91.125  125.     166.375]

f = interp1d(x, y, "quadratic")
print f(xnew)

OUTPUT
[   8.    15.5   27.    43.    64.    91.   125.   166.5]

```

## 2D interpolation
```python

from scipy import random, mgrid
from scipy.interpolate import griddata
def f(x, y):
    return x + y

grid_x, grid_y = mgrid[0:1:5j, 0:1:5j]
points = random.rand(25, 2)
values = f(points[:, 0], points[:, 1])

print griddata(points, values, (grid_x, grid_y), method="cubic")


OUTPUT
[[  nan   nan   nan   nan   nan]
 [  nan  0.5   0.75  1.     nan]
 [  nan  0.75  1.    1.25   nan]
 [  nan  1.    1.25  1.5    nan]
 [  nan   nan   nan   nan   nan]]

 

print griddata(points, values, (grid_x, grid_y), method="nearest")
OUTPUT
[[ 0.15816536  0.15816536  0.6364253   0.85283824  1.0880222 ]
 [ 0.33930886  0.33930886  0.79653985  1.0387893   1.0880222 ]
 [ 0.75785667  0.93651026  1.02458428  1.24200854  1.4936412 ]
 [ 0.75785667  0.75785667  1.32061996  1.33740459  1.6481689 ]
 [ 0.75785667  1.34710428  1.34710428  1.77777691  1.77777691]]

```
Video
[![](http://img.youtube.com/vi/s-3l_527ydQ/0.jpg)](http://www.youtube.com/watch?v=s-3l_527ydQ "")