# Pure CSS Island

> A 3D island with animated parts and camera rotation.

A demo can be found [here](https://codepen.io/honmanyau/full/vpzqpr) on CodePen. It was picked on 2017.01.16!

Tested with Chrome 63 and Firefox 57. No support for IE. Please toggle animation off with the checkbox above if you see glitches (for example, Safari 11.0.2 and Safari 11 on iOS).

## Description

The 3D effect is achieved using multiple CSS grids, a bunch of which are transformed to be evenly spaced, and parallel, to each other on the x-y, x-z and y-z planes, which ultimately forms a cube.

Multiple cubes of the type made as described above are used either for convenience (such as the objects above ground) or to avoid animation glitches caused by overlapping grids (at least for both Chrome and Firefox).

There are two ways in which the cubes and rectangular prisms are created: 1. positioning squares or rectangles (with grid-column and grid-row) onto the appropriate grid in the x-y, x-z and y-z planes (the bottom square or rectangle are often omitted for performance reasons, even though there is already little to speak of); 2. applying the correct transformation (mostly rotations and scaling) onto multiple absolutely positioned squares or rectangles.

The first method described above is used to make the water body and the base of the island because, at least at the time of creating this, I felt that the structures are large enough that it's easier to edit/maintain. The second method described is less consistent in terms of nomenclature used for classes in the first method, but substantially reduces the CSS that needs to be written and are used mostly on the above-ground objects because of that reusability (for example, the stairs are grouped using a div and are simply rotated, translated, and recoloured copies).

Getting the coordinate system "right" is, in my opinion, the key to reducing the amount of code that needs to be written. The current code is very far from this ideal because it was actually an experiment to begin with and I naively started without using a CSS pre-processor and, admittedly, at some point the rotation became a bit too time-consuming to think about that I just wanted to finish it for the artistic value of it.

The camera controls and animation toggle take advantage of the general sibling CSS selector and the :checked pseudo-class selector to preferentially apply transitional CSS transformation to the div that contains all the visible elements.

Another thing that is perhaps worth mentioning is that most of the elements (with the exception of the top of the triangular pillars because I couldn't think of a way that doesn't involve borders at the time) are relatively sized with respect to the original size of each CSS grid (400 px in this case). The trick to this is to first rotate an element by 90 degrees along the x or y axis, translate it by the desired amount in the orthogonal axis in the same plane, and then undo the rotation; if I'm not mistaken, it would otherwise not be possible to size everything relatively.

It was overall an interesting experiment and a fun 3D puzzle, and is also great way to practice CSS grid and "spatial reasoning".
