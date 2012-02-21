Carrying out geometric transformations using matrices
=====================================================

Using SAGE for Matrix Transformations
-------------------------------------

This chapter tells you how to use the free and Open-Source `SAGE mathematics software <http://www.sagemath.org/>`_
for studying geometric transformations using matrices.

To use SAGE, you first need to start the SAGE program on your computer.
You should have already installed SAGE on your computer (if not, for instructions on how to
install SAGE, see `the SAGE Installation Guide <http://www.sagemath.org/doc/installation/>`_).

This booklet assumes that the reader has some basic knowledge of matrix transformations,
and the principal focus of the booklet is not to explain matrix transformations,
but rather how to study matrix transformations using SAGE.

If you are new to matrix transformation, and want to learn more about any of the concepts presented here, 
I would highly recommend the Open University book “Matrix transformations” (product code MS221 chapter B2), 
available second-hand from from the `Open University Book Search <http://www.universitybooksearch.co.uk/>`_.

Vectors in SAGE
---------------

We can enter vectors a and b into SAGE by typing:

::

    a = vector([4,3])
    print(a)
    # Output: 
    # (4, 3)
    b = vector([-5,2])
    print(b)
    # Output: 
    # (-5, 2)

We can then combine the vectors algebraically, for example, we can calculate
2a + (3/2)b by typing:

::

    c = (2*a) + ((3/2)*b)
    print(c)
    # Output: 
    # (1/2, 9)

If P is a point in the plane, then the position vector p from the origin (0,0) to point P is
called the position vector of P (with respect to the origin).

For example, if we have a triangle with vertices at points (1, sqrt(3)), (sqrt(3), -1),
and (-sqrt(3),1), then we can represent the triangle by the three position vectors p1, p2 and
p3 representing these three vectices:

::

    p1 = vector([1, sqrt(3)])
    p2 = vector([sqrt(3), -1])
    p3 = vector([-sqrt(3), 1])

If we want to make a plot of a polygon (a triangle here) defined by certain position vectors,
we can type in SAGE:

::

    mypoints = list([p1,p2,p3])
    P = polygon(mypoints)
    P.set_aspect_ratio(1)
    show(P)

|image7|

Note that the set_aspect_ratio() command ensures that the scale on the x-axis and y-axis of the plot
are the same.

Translation of a polygon
------------------------

We can carry out a translation of a polygon, by addition of a vector a = (p, q). For example, the
vector a = (2, 3) will move a shape two units to the right and three units up. 

Let's write a function to apply a translation to a polygon:

::

    def translate_polygon(mypoints, a):
       mypoints2 = []
       for mypoint in mypoints:
          mypoint2 = mypoint + a
          mypoints2.append(mypoint2)
       return(mypoints2)

We can then move the triangle defined above two units to the right and three units upwards
by applying the transformation described by vector a:

::

    a = vector([2, 3])
    mypoints2 = translate_polygon(mypoints, a)

Let's plot the original triangle (in blue) and the translated triangle (in green):

::

    P = polygon(mypoints) + polygon(mypoints2,color="green")
    P.set_aspect_ratio(1)
    show(P)

|image10|

The original triangle is shown in blue here, and the transformed one in green.

Matrices in SAGE
----------------

We can enter a matrix A into SAGE by typing:

::

    A = matrix([[2,1],[3,2]])
    print(A)
    # Output: 
    # [2 1]
    # [3 2]

We can then do nice things like multiplying a vector by a matrix:

::

    a = vector([2, 3])
    A = matrix([[2,1],[3,2]])
    a * A
    # (13, 8)

Rotation of a polygon
---------------------

A rotation of a polygon, through an angle theta (radians) anticlockwise, can be obtained by
multiplying the matrix:

|image13|

xxx with rows (cos theta, -sin theta) and (sin theta, cos theta) by each point defining the polygon
(for example, by each of the three points defining the vertices of a triangle).

This means that we can define a function to perform such a rotation of a polygon:

::

    def rotate_polygon(mypoints, theta):
       A = matrix([[cos(theta),-(sin(theta))],[sin(theta),cos(theta)]])
       mypoints2 = []
       for mypoint in mypoints:
          mypoint2 = A* mypoint
          mypoints2.append(mypoint2)
       return(mypoints2)

Let's try rotating our triangle above by pi/4 radians (45 degrees) anticlockwise:

::

    mypoints3 = rotate_polygon(mypoints, pi/4)

Let's plot the original triangle (in blue) and the rotated triangle (in green):

::

    P = polygon(mypoints) + polygon(mypoints3,color="green")
    P.set_aspect_ratio(1)
    show(P)

|image11|

Reflection of a polygon
-----------------------

A reflection of a polygon in a line through the origin that makes an angle theta measured anticlockwise from the positive x-axis,
can be achieved by multiplying the matrix with rows (cos(2 * theta), sin(2 * theta)) and (sin(2 * theta), -cos(2 * theta))
by each of the points that define the polygon (eg. by each of the three vertices of a triangle).

Aha! That means that we can define a function to carry out a reflection of a polygon:

::

    def reflect_polygon(mypoints, theta):
       A = matrix([[cos(2*theta),sin(2*theta)],[sin(2*theta),-(cos(2*theta))]])
       mypoints2 = []
       for mypoint in mypoints:
          mypoint2 = A* mypoint
          mypoints2.append(mypoint2)
       return(mypoints2)

For example, let's reflect the triangle with vertices at (1, sqrt(3)), (sqrt(3), -1),
and (-sqrt(3),1), through a line that makes an angle of pi/4 radians (45 degrees) with respect to the positive x-axis:

::

    mypoints4 = reflect_polygon(mypoints, pi/4)

Now let's plot the original triangle (in blue) and the transformed triangle (in green), with the line
that the triangle was reflected through (in red):

::

    P = polygon(mypoints) + polygon(mypoints4,color="green") + plot(x, (x, -2, 2), color="red")
    P.set_aspect_ratio(1)
    show(P)

|image12|

Scaling of a polygon
--------------------

A scaling of a polygon by factor a parallel to the x-axis, and by factor b parallel to the y-axis, can 
be achieved by multiplication of the matrix with rows (a, 0), and (0, b) by each of the points that
define the polygon (for example, by each of the vertices of a triangle).

Let's define a SAGE function to scale a polygon like this:

xxx

For example, we can scale our triangle with vertices at (1, sqrt(3)), (sqrt(3), -1),
and (-sqrt(3),1), by a factor 3 parallel to the x-axis, and by a factor 6 parallel to the y-axis by typing:

xxx

Links and Further Reading
-------------------------

Some links are included here for further reading.

For background reading on matrix transformations, I would recommend the Open University book “Matrix transformations” 
(product code MS221 chapter B2), available second-hand from from the 
`Open University Book Search <http://www.universitybooksearch.co.uk/>`_.

For an in-depth introduction to SAGE, see the `SAGE documentation website <http://www.sagemath.org/help.html#SageStandardDoc>`_.

Acknowledgements
----------------

xxx remove aknowl

Thank you to Noel O'Boyle for helping in using Sphinx, `http://sphinx.pocoo.org <http://sphinx.pocoo.org>`_, to create
this document, and github, `https://github.com/ <https://github.com/>`_, to store different versions of the document
as I was writing it, and readthedocs, `http://readthedocs.org/ <http://readthedocs.org/>`_, to build and distribute
this document.

Many of the examples in this document have been inspired by examples in the excellent Open University
book “Matrix transformations” (product code MS221 chapter B2), available second-hand from from the 
`Open University Book Search <http://www.universitybooksearch.co.uk/>`_.

Contact
-------

I will be grateful if you will send me (`Avril Coghlan <http://www.ucc.ie/microbio/avrilcoghlan/>`_) corrections or suggestions for improvements to
my email address a.coghlan@ucc.ie 

License
-------

The content in this book is licensed under a `Creative Commons Attribution 3.0 License
<http://creativecommons.org/licenses/by/3.0/>`_.

.. |image7| image:: ../_static/image7.png
.. |image9| image:: ../_static/image9.png
.. |image10| image:: ../_static/image10.png
.. |image11| image:: ../_static/image11.png
.. |image12| image:: ../_static/image12.png
.. |image13| image:: ../_static/image13.png
.. |image300| image:: ../_static/image1.png
            :width: 900



