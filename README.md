# perlin-noise

### Research Links
+ Perlin Noise: https://en.wikipedia.org/wiki/Perlin_noise
+ Understanding Perlin Noise: https://adrianb.io/2014/08/09/perlinnoise.html
+ Unit cubes/squares: https://gamedev.stackexchange.com/questions/179573/dividing-coordinate-into-unit-cube
+ C++ Reference: https://www.w3schools.com/cpp/default.asp

### Perlin Noise Research
Implemented as a N-dimensional function. We will be implementing a 2D function.

1) Define a grid of random grandient vectors (What is a gradient vector?)
    - Define an 2D grid
    - Each grid intersection should be associated with a fixed random 2D unit-length gradient vector

    - Divide input coordinate (x; y) into unit squares => (x, y) % 1.0
    - This calculation allows us to find the coordinate location within the square (what square? what bounds  the square?)
    - So for an input coordinate (x, y) we compute (x, y) % 1.0, which yields the point inside a square bounded by integral coordinates
    - Where integral coordinates refer to coordinates which are whole numbers

    - For each of the 4 integral (unit coordinates?) we need to generate a psuedorandom gradient vector
    - I can only assume that we are required to determine the gradient vector between each integral point and unit square we calculated earlier
    - Where an integral point could be (x0, y0) and our unit square (xs, ys) with gradient vector = (x0 - xs, y0 - ys)
    - Then this gradient vector is associated with the integral coordinate used in its calculation as the vector being drawn from the integral coordinate
    - Hence the earlier statement, "Each grid intersection should be associated with a fixed random 2D unit-length gradient vector"
2) Compute the dot product between gradient vectors and their offsets (what does the offest of a gradient vector refer to?)
3) Interpolate between the computed values in (2) (How does one interpolate between 2 or more values?)

### Conceptual Design


### Technical Design