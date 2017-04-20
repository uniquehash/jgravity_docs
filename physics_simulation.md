# physics simulation

detailed below is not the final system for the simulation by any means. we can think of it as the naive approach to building this simulation.

it is important to understand that the fundemental insight of the janus model rests on the fact that simply having a negative mass to represent "anti-material" should allow us to use all the same mathematics as we normally would, but give us better results at scale.

it is important that we conceive our simulation working in steps of time of arbritary uniform length. this allows us to granully alter the speed of change in our simulation, allowing us to have fine tune control over it's fluidity. 

calculating the influence of gravity on a star is the same for clusters of stars as it is for two arbritary objects. basically we use the same math but aggregate the mass and coordinates of all the stars influencing the object of focus. this creates a new mass and a new set of coordinates corresponding to the center of gravity of the sum of the influencing forces. introducing the "anti-material" or negative material does not change this in the slightest. since it is represented by negative mass it will naturally represent the effects of interaction between our two types of matter without any additional mathematics. 

every star in our system has a **sphere of influence** which is a radius from the star's coordinates in all 3 dimensions that represent the area in which that particular star's gravitational influence is measurable. this radius is derived from the mass in some fashion (not yet figured out).

the first step in implementing the physics simualation is determining which stars influence what. to do so we iterate through each star, checking to see if any other stars coordinates are within the current stars **sphere of influence**. for every star detected within the **sphere of influence** we add a node to a linked list of `influencing_stars` in the detected star. this node contains the mass and coordinates of the current star (that which is doing the detecting). we do this for every star in the system.

next we must iterate through each star again, this time to calculate the coordinates in the next interval. this is relatively simple once fully groked, but may be confusing at first. 

by this point every star in our system should contain a linked list `influencing_stars` contain 0 or more elements. it is this list that we will aggregate into our center of gravity that will influence the current star.

* to find the aggregate mass
  * sigma_mass = i = 1 sigma (mass(i))
* to find the coordinates of the center of gravity
  * sigma_x = (sigma x(i) * mass(i)) / sigma(mass(i))
  * sigma_y = (sigma y(i) * mass(i)) / sigma(mass(i))
  * sigma_z = (sigma z(i) * mass(i)) / sigma(mass(i))

these will be the values we use to find the gravitational influence on the current star from it's neibhoring star, and determine it's coordinates in the next interval.

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
  * fX = ((massB * (6.673 * pow(10, -11) / pow(const_distance, 3))) * (xB - xA))
  * fY = ((massB * (6.673 * pow(10, -11) / pow(const_distance, 3))) * (yB - yA))
  * fZ = ((massB * (6.673 * pow(10, -11) / pow(const_distance, 3))) * (zB - zA))
* distance
  * sqrt(pow(xA - xB, 2) + pow(yA - yB, 2) + pow(zA - zB, 2))

we repeat this process for every interval of time until the universe breaks or we get bored.

this design does not attempt to optimize in anyway, whether they be in multi-threading, multi-process, or multi-server optimization.















