Problem summary
---------------

Create a function `slope` that takes a vector of x-locations and a vector
of y-locations and calculates the slope (dy/dx) at each x-location.


Solution
--------

The full source code of a solution (using the
`Numeric` package, so there are a few differences) is
[here](http://www.johnny-lin.com/py_pkgs/gemath/lib/deriv.py); it's
a good reference from a structure and commenting standpoint.  It also
contains a bunch of extra complications that give a more flexible and
general solution (including handling missing values) than the assignment
called for.  The meat of it could be summarized here:

    def slope(y, x):
        import numpy as N
        x_endpadded = N.zeros(N.size(x)+2, dtype=x.dtype.char)
        x_endpadded[0]    = x[0]
        x_endpadded[1:-1] = x 
        x_endpadded[-1]   = x[-1]

        y_endpadded = N.zeros(N.size(y)+2, dtype=y.dtype.char)
        y_endpadded[0]    = y[0]
        y_endpadded[1:-1] = y
        y_endpadded[-1]   = y[-1]

        y_im1 = y_endpadded[:-2]
        y_ip1 = y_endpadded[2:]
        x_im1 = x_endpadded[:-2]
        x_ip1 = x_endpadded[2:]

        return (y_ip1 - y_im1) / (x_ip1 - x_im1)

Most of the function is devoted to creating working arrays (the
`endpadded` arrays) that are consistent with a 3-point stencil in the
interior and 2-point stencil on the ends.  The `im1` means the point
before index i, `ip1` means the point after index i, and the i index
array is just plain x or y.  This way I'm able to avoid using a `for`
loop or conditional statements.

The `dtype` keyword arguments are used to ensure the `endpadded` versions
are the same type as the input.

Note by using array slicing to set the `endpadded` versions I end up
making a separate copy instead of a reference to `x` and `y` (do a Google
search to find and read the `numpy` manual for details).
