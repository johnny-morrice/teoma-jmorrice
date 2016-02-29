+++
date = "2016-02-29T17:39:09Z"
draft = false
title = "Godelbrot Region Render Algorithm"
importance = "interest"
genre = ["prose", "maths"]
projects = ["Godelbrot"]
+++

# Rendering the Mandelbrot Set with Subdividing Regions

If you look at the mandelbrot set (like the Godelbrot web interface) you will notice that some parts of the image are less complicated than other parts.

![Godelbrot Rendering](/image/mandelbrot-sameness.png)

The yellow, cloud like shapes occupy large regions of space.  There is also a lot of black (set members) in the image.  With the Go image library, as with many other image rendering packages, it takes many instructions to colour each output pixel individually.  It is much more efficient to draw large regions of the same colour at one time.  There seems to be some potential for optimization here.

Unfortunately, the non-linear nature of the Mandelbrot set means efficent drawing is near-impossible to solve in general.  In practise however, I have found the following greedy space partitioning algorithm works well.

![Radius of sameness](/image/mandelbrot-radius.png)

In analysis, we would probably begin by imagining a circle around the point on the plane.  This because radius is naturally a great way to express proximity.  On the computer we would rather use rectangles, because they are easy to represent.  Our rendering is done on the CPU.  I am not an expert in GPU programming, but my limited experience with OpenGL makes me think that rectangles would also be a good fit on that hardware.

![Rectangles are easier](/image/mandelbrot-rectangle.png)

How do we know that every point on a rectangle has equal inverse divergence?  One dumb way of doing this is to check a subset of points.  If each point in the sample has an equal Inverse Divergence Rate, assume that the whole is equal.  Call this "Relatively Samey".  If not, recurse.  In this manner, we recursively partition the space into successively smaller rectangles.

We first tried to be as dumb as possible in our determination of "Relative Sameness".  We merely checked the corners and centre of the region, since these have pre-computed inverse divergence.  We found this lead to glitches, so we broadened the approach to include a number of samples from
across the region.  The number of samples is given by a user parameter.

![Subdivision](/image/mandelbrot-subdivide.png)

When a rectangle is assumed to be "Relatively Samey", we can mark the appropriate location on the output image with a single method call.  If not, you will eventually recurse until your rectangle covers a tiny area.  As a set of recursively partitioned rectangles is a heavy structure for covering a small area, in Godelbrot we allow the user to define a minimum subdivision size.  Any rectangle which is below this size will instead be rendered by the Sequence algorithm.

The downsides of the region method is that it is fairly complex.  It has branches in sections of the code where we would like to stream straight ahead.  If you are not careful, in creating the datastructure objects, you can generate a lot of garbage which then needs to be freed.

With respect to native CPU arithmetic, after profiling this algorithm, we found it is memory bound.  Shifting the required datastructures around consumes a lot of time in comparison to actually computing the Mandelbrot set.  As one who is familiar with Chaos theory might expect, performance is variable.  However, I regularly observe a time reductions of ~50% compared with the naive pixel-by-pixel method.  It is especially notable at high resolutions, where large and featureless regions can be skipped.  It is important to note that this optimization, like audio compression, relies partly on psychology.  It sure looks like the Mandelbrot set, but if you don't compute it pixel by pixel, can you really say it is so?