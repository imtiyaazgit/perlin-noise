# perlin-noise

### Research Links
+ Perlin Noise: https://en.wikipedia.org/wiki/Perlin_noise
+ Understanding Perlin Noise: https://adrianb.io/2014/08/09/perlinnoise.html
+ Unit cubes/squares: https://gamedev.stackexchange.com/questions/179573/dividing-coordinate-into-unit-cube
+ C++ Reference: https://www.w3schools.com/cpp/default.asp
+ Lerp Equation: https://www.cuemath.com/linear-interpolation-formula/

### Perlin Noise Research
Implemented as a N-dimensional function. We will be implementing a 2D function.

1) Determining Unit Squares between integral coordinates
    - Define an 2D grid
    - Each grid intersection should be associated with a fixed random 2D unit-length gradient vector

    - Divide input coordinate (x; y) into unit squares => (x, y) % 1.0
    - This calculation allows us to find the coordinate location within the square (what square? what bounds  the square?)
    - So for an input coordinate (x, y) we compute (x, y) % 1.0, which yields the point inside a square bounded by integral coordinates
    - Where integral coordinates refer to coordinates which are whole numbers

2) Define a grid of random grandient vectors (What is a gradient vector?)
    - For each of the 4 integral (unit coordinates?) we need to generate a psuedorandom gradient vector
    - Psuedorandom refers to a gradient vector generating equation being able to always generate the same gradient vector for the same input, since the RNG always uses the same seed
    - Ultimately, this means our gradient vector function must always return the same gradient vector for the same integral grid point
    - Having the same seed guarentees we always get back the same sequence of "random" numbers for each generation
    - Hence the earlier statement, "Each grid intersection should be associated with a fixed random 2D unit-length gradient vector"

3) Compute the dot product between gradient vectors and their offsets (what does the offest of a gradient vector refer to?)
    - Firstly we need to determine the distance vectors
    - Distance vectors refer to the vectors taken from each of the integral points to the point calculated in (1)
    - The point calculated in (1) being the point that is bounded by the set of 4 integral points that form a square around it
    - Once these distance vectors are calculated we can now perform the dot product between the distance vectors and gradient vectors for each integral point in the grid
    - Remember, each integral point is now associated with a gradient vector and distance vector emenating from it
    - The dot product between gradient and distance vectors is referred to as influence values

3) Interpolate between the computed values in (3) (How does one interpolate between 2 or more values?)
    - Now we need to interpolate between 4 influence values assocaited with a squares integral coordinates
    - We will perform linear interpolation between points
    - Linear interpolation refers to deducing a value between 2 explicitly defined values on a table/grid
    - In mathematics, linear interpolation is a method of curve fitting using linear polynomials to construct new data points within the range of a discrete set of known data points.
    - In other words, lerping allows us to generate new points between a set of know points which leads to a smoother curve between all points.
    - We usually lerp between 2 points, but since we have 4 points (integral points) we lerp between the top coordinates of the square using the the x of the point in (1) as its lerp point -> A
    - Then we lerp between the bottom coordinates of the square with the x of the point in (1) as its lerp point -> B
    - Finally, we lerp between A and B using the y of point in (1)

4) But before lerping, we need to apply a easing function to the point in (1) to provide a more natural smoothing to the interpolation performed above
    - We can use the following function to fade a value **6t^5-15t^4+10t^3**

### Conceptual Design


### Technical Design