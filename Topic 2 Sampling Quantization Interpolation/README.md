# DIP: Digital image processing


## Sampling, Quantization and Interpolation

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

[![Watch the video](https://github.com/tinkerslab/DIP/blob/master/raw_data/2D_interpolation.png)](https://github.com/tinkerslab/DIP/blob/master/raw_data/2D_interpolation.mp4)

<!-- blank line -->
<figure class="video_container">
  <iframe src="https://github.com/tinkerslab/DIP/blob/master/raw_data/2D_interpolation.mp4" frameborder="0" allowfullscreen="true"> </iframe>
</figure>
<!-- blank line -->