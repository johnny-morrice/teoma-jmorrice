+++
date = "2016-08-02T22:49:54+01:00"
draft = false
title = "Mixing Paint: A Vector Tutorial For Beginners"
genre = ["maths", "tutorial"]
importance = "interest"
+++

# A beginner's introduction to vectors, using paint

Everyone knows that if you take three primary colours, red, yellow, and blue, you can mix them to get any other colour.

We know that:

`red + yellow = orange`

`red + blue = purple`

`yellow + blue = green`

Look at the right hand side of these equations.  Nothing about the word `green` tells you anything about the primary colours that made it.  That's not very useful right?  

What if you wanted to know the difference between `Forest Green` and `Apple Green`.  Nothing about those names tells you how much `red`, `yellow`, and `blue` went into them.  

For that, you should use vectors.

A colour vector is just three numbers in a list.  

* The first number describes how much red paint was used.  
* The second says how much yellow paint was used.  
* The third says how much blue was used.

We put the list in brackets.

`(red, yellow, blue)`

 We'll try writing some colours as vectors now, starting with the primary colours to keep things simple.

`red = (1, 0, 0)`

*(the 1 stands for how much red paint we used compared to 0 yellow and blue.)*

`yellow = (0, 1, 0)`

`blue = (0, 0, 1)`

Now instead of writing the name of a colour, we can write the degree to which it is mixed from the three primary colours.  

But how do we mix them?  Well, you have the two vectors, and you just add each number that shares the same position.  For example:

`red + yellow = orange` is the same as `(1, 0, 0) + (0, 1, 0) = (1, 1, 0)`

so

`orange = (1, 1, 0)`

`red + blue = purple` is the same as `(1, 0, 0) + (0, 0, 1) = (1, 0, 1)`

so

`purple = (1, 0, 1)`

and

`yellow + blue = green` is the same as `(0, 1, 0) + (0, 0, 1) = (0, 1, 1)`

so `green = (0, 1, 1)`.

## End of lesson

Future topics:

* Paintings are grids of colour vectors
* Red, yellow, and blue aren't the only possible primary colours!
* Transparency and the fourth dimension
