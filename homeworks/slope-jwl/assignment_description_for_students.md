Create a function `slope` that takes a vector of x-locations and a vector
of y-locations and calculates the slope (dy/dx) at each x-location. The
output will be a vector of the same size and shape as the x-location
vector. In the code below, `dydx` will be the slope at each x location:

    import numpy as N
    x = N.array([0, 1, 2, 3, 4])
    y = N.array([-20.1, -2.9, 1.5, 3.2, -1.3])
    dydx = slope(y, x)

This function should work with irregularly spaced x-locations. You can
assume the x-location vector is sorted ascending. You'll have to think
hard though about how you'll treat the endpoints of the vector (this is
an example of a classic issue in scientific computing, how to deal with
boundary conditions).

Make sure you include adequate, appropriate, and complete
documentation. This includes a docstring for the function
as well as comment lines in the code. For an example of
adequate documentation, see [this routine to calculate mixing
ratio](http://www.johnny-lin.com/py_pkgs/atmqty/lib/mix_ratio.py). (Don't
worry if you don't know what mixing ratio is; just pay attention to the
documentation.) I'm not expecting your documentation to be this complete,
but this is what I'd like you to be working towards.
