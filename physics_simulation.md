# Physics Simulation

Detailed below is not the final system for the simulation by any means. We can think of it as a naive approach to building this simulation.

It is important to understand that the fundemental insight of the janus model rests on the fact that simply having a negative mass to represent "anti-material" should allow us to use the same mathematics as we normally would use and give us better results at scale.

It is important that we conceive our simulation working in steps of time of arbritary uniform length. This allows us to granually alter the speed of change in our simulation, which will give us fine tune control over it's fluidity.

Calculating the influence of gravity on a star is the same for clusters of stars as it is for two arbritary objects. Basically we use the same math, but aggregate the mass and coordinates of all the stars influencing the object of focus. This creates a new mass and a new set of coordinates corresponding to the center of gravity of the sum of the influencing forces. Introducing the "anti-material"(negative material) does not change this in the slightest. Since it is represented by negative mass, it will naturally represent the effects of interaction between our two types of matter without any additional mathematics. 

Every star in our system has a **Sphere Of Influence** which is a radius from the star's coordinates in all 3 dimensions that represent the area in which that particular star's gravitational influence is measurable. This radius is derived from the mass in some fashion (to be determined).

The first step in implementing the physics simualation is determining which each star influences. To do so, we iterate through each star, checking to see if any other stars coordinates are within the current stars **Sphere Of Influence**. For every star detected within the **Sphere Of Influence** we add a node to a linked list of `influencing_stars` in the detected star. This node contains the mass and coordinates of the current star (that which is doing the detecting). We do this for every star in the system.

Next we must iterate through each star again, this time to calculate the coordinates in the next interval. This is relatively simple once fully understood, but may be confusing at first. 

By this point every star in our system should contain a linked list `influencing_stars` containing 0 or more elements. It is this list that we will aggregate into our center of gravity that will influence the current star.

* to find the aggregate mass
  * sigma_mass = i = 1 sigma (mass(i))
* to find the coordinates of the center of gravity
  * sigma_x = (sigma x(i) * mass(i)) / sigma(mass(i))
  * sigma_y = (sigma y(i) * mass(i)) / sigma(mass(i))
  * sigma_z = (sigma z(i) * mass(i)) / sigma(mass(i))

To start however, we can ignore this concept of **Sphere Of Influence** and simply have every star interacting with each other. Implementation wise this will be far simpler. The trick is to have a global struct which contains the aggregate mass of the system, and the coordinates of the aggregate center of mass. Then as we iterate through each star in the system to calculate the gravitational influence of the system on the current star we subtract the current stars mass from the aggregate mass and remove it's position from the coordinates of the aggregate center of mass. 

* finding the mass influencing the star
  * influencing_mass = sigma_mass - mass
* finding the coordinates of the influencing center of gravity
  * influencing_x = ((sigma_x * sigma_mass) - (mass * x)) / (influencing_mass)
  * influencing_y = ((sigma_y * sigma_mass) - (mass * y)) / (influencing_mass)
  * influencing_z = ((sigma_z * sigma_mass) - (mass * z)) / (influencing_mass)

Basically, we use a global to contain all of the aggregate information and then subtract the current stars information from it to determine all the stars influencing the current stars, some of these stars will have 0 or near 0 impact on the current star, this however is a simpler way to implement this until we understand the physics of the problem a little bit better. 

These will be the values we use to find the gravitational influence on the current star from it's neighboring star, and determine it's coordinates in the next interval.

**delta_t** is the length of time that our simulation uses. 

* coordinates 
  * x = x + delta_X
  * y = y + delta_Y
  * z = z + delta_Z
* delta coordinates
  * delta_X = vX * delta_t
  * delta_Y = vY * delta_t
  * delta_Z = vZ * delta_t
* velocity
  * vX = vX + delta_vX
  * vY = vY + delta_vY
  * vZ = vZ + delta_vZ
* delta velocity
  * delta_vX = fX * delta_t
  * delta_vY = fY * delta_t
  * delta_vZ = fZ * delta_t
* forces
  * fX = (((massA / abs(massA)) * massB * (6.673 * pow(10, -11) / pow(const_distance, 3))) * (xB - xA))
  * fY = (((massA / abs(massA)) * massB * (6.673 * pow(10, -11) / pow(const_distance, 3))) * (yB - yA))
  * fZ = (((massA / abs(massA)) * massB * (6.673 * pow(10, -11) / pow(const_distance, 3))) * (zB - zA))
* distance
  * sqrt(pow(xA - xB, 2) + pow(yA - yB, 2) + pow(zA - zB, 2))

We repeat this process for every interval of time until the universe breaks, or we get bored.

This design does not attempt to optimize in anyway, whether they be in multi-threading, multi-process, or multi-server optimization.
