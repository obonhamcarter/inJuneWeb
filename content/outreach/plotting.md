---
title: "Plotting"
date: 2023-03-16T23:40:01-04:00
draft: False
---

<center>
&#x200B;
<img src="/images/outreach/plotting.png" alt="A Futuristic Classroom" style="width:700px;"/>
</center>

<!-- add a line drop -->
<center>
&#x200B;
</center>

We will spend a moment to study different ways of visually describing data using plots. Here we will develope some Python programming techniques to create some data to be used for plotting. In specific, we will look at several types of plots and then decide what types of features each plot has and how it could be helpful when describing data.

### Making random data for plotting
We first begin by making come random data which we could use for plotting later. There are different types of data to create. For instance, we will make data from several types of __distributions__. A [distribution](https://www.ibm.com/docs/en/SSEP7J_11.1.0/com.ibm.swg.ba.cognos.ug_ca_dshb.doc/statisticaldistribution.html) type provides a statistical vocabulary which describes which values are common, and which are uncommon for a field of numbers.

---


## Normal Distribution

``` python
x_axis = np.arange(-20, 20, 0.01)
  
# Calculating mean and standard deviation
from numpy import random

mean = statistics.mean(x_axis)
sd = statistics.stdev(x_axis)
norm.pdf(x_axis, mean, sd)

x = random.normal(size=(2, 3))
print(x)
```

### Line

``` python
import numpy as np
import matplotlib.pyplot as plt
from scipy.stats import norm
import statistics
  
# Plot between -10 and 10 with .001 steps.
x_axis = np.arange(-20, 20, 0.01)
  
# Calculating mean and standard deviation
mean = statistics.mean(x_axis)
sd = statistics.stdev(x_axis)
age = norm.pdf(x_axis, mean, sd)

# x-axis label
plt.xlabel('age')
# frequency label
plt.ylabel('No. of people')
# plot title
plt.title('A Normal Distribution')

plt.plot(x_axis, age )
plt.show()
```

### Histogram

``` python
import numpy as np
import matplotlib.pyplot as plt
from scipy.stats import norm
import statistics
  
# Plot between -10 and 10 with .001 steps.
x_axis = np.arange(-10, 10, 0.01)
ages = random.normal(size=(2000,1))

# x-axis label
plt.xlabel('age')
# frequency label
plt.ylabel('No. of people')
# plot title
plt.title('A Normal Distribution')

plt.plot(x_axis, ages)
plt.show()
```


## Binomial Distribution

``` python
from numpy import random
x = random.binomial(n=10, p=0.5, size=10)
print(x)
```


### Histogram (Bar Chart)

``` python
from numpy import random
import matplotlib.pyplot as plt

# frequencies
ages = list(random.binomial(n=10, p=0.5, size=1000))
print(f"The data in the variable ages : {ages}, {type(ages)}")  
 
# setting the ranges and no. of intervals
range = (0, 10)
bins = 50

# plotting a histogram
plt.hist(ages, bins, range, color = 'blue', histtype = 'bar', rwidth = 0.8)
  
# x-axis label
plt.xlabel('age')
# frequency label
plt.ylabel('No. of people')
# plot title
plt.title('A Binomial Distribution')
  
# function to show the plot
plt.show()
```

---

## Poisson Distribution

``` python
from numpy import random
x = random.poisson(lam=2, size=10)
print(x)
```


### Histogram

``` python
from numpy import random
import matplotlib.pyplot as plt

# frequencies
ages = random.uniform(size=(2, 10)) #size(y_max, x_iterations)
print(f"The data in the variable ages : {ages}, {type(ages)}")  
 
# setting the ranges and no. of intervals
range = (0, 20)
bins = 1

# plotting a histogram
plt.hist(ages, bins, range,  histtype = 'bar', rwidth = 1)
  
# x-axis label
plt.xlabel('age')

# frequency label
plt.ylabel('No. of people')

# plot title
plt.title('A Uniform Distribution')
  
# function to show the plot
plt.show()
```

---

## Uniform Distribution

``` python
from numpy import random
#x = random.uniform(size=(2, 3))
ages = list(random.uniform(size=(2, 3)))#lam=2, size=100

print(x)
```


### Histogram

``` python
from numpy import random
import matplotlib.pyplot as plt

# frequencies
ages = random.uniform(size=(2, 3))#lam=2, size=100
print(f"The data in the variable ages : {ages}, {type(ages)}")  
 
# setting the ranges and no. of intervals
range = (0, 10)
bins = 10

# plotting a histogram
plt.hist(ages, bins, range, color = 'blue', histtype = 'bar', rwidth = 0.8)
  
# x-axis label
plt.xlabel('age')

# frequency label
plt.ylabel('No. of people')

# plot title
plt.title('A Poisson Distribution')
  
# function to show the plot
plt.show()
```