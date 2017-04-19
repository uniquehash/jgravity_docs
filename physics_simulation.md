# physics simulation

it is important to understand that the fundemental insight of the janus model rests on the fact that simply having a negative mass to represent "anti-material" should allow us to use all the same mathematics as we normally would, but give us better results at scale.

it is important that we conceive our simulation working in steps of time of arbritary uniform length. this allows us to granully change the speed of change in our simulation, allowing us to have fine tune control over it's fluidity. 

calculating the influence of gravity on a star is the same for clusters of stars as it is for two arbritary objects. basically we use the same math but aggregate the mass and coordinates of all the stars influencing the object of focus. this creates a new mass and a new set of coordinates corresponding to the center of gravity of the sum of the influencing forces. introducing the "anti-material" or negative material does not change this in the slightest. since it is represented by negative mass it will naturally represent the effects of interaction between our two types of matter without any additional mathematics. 

every star in our system has a "**sphere of influence**" which is a radius from the star's coordinates in all 3 dimensions that represent the area in which that particular star's gravitational influence is measurable. this radius is derived from the mass in some fashion (not yet figured out).

the first step in implementing the physics simualation is determining which stars influence what. to do so we iterate through each star, checking to see if any other stars coordinates are within the current stars **sphere of influence**. for every star detected within the **sphere of influence** we add a node to a linked list of `influencing_stars` in the detected star. this node contains the mass and coordinates of the current star (that which is doing the detecting). we do this for every star in the system.

next we must iterate through each star again, this time to calculate the coordinates in the next interval.







