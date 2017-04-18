# first principles
the goal is to build a system that implements these principles


#### gravatational particle interaction in the janus model
1. 2 types of particles
   * positive
   * negative
2. particles of the same type attract
   * |positive| ---> <--- |positive|
   * |negative| ---> <--- |negative|
3. particles of different types repel
   * <--- |positive||negative| --->
---

#### properties of stars
* arbritary masses
* flag to represent either positive or negative particle
* x, y, z current position
* velocity for x, y, z
* sphere of influence derived from mass
  * this is the distance from the particle in which other particles are influenced
* to calculate new coordinates
  * aggregate all forces acting on the star
  * perform the gravitational equation between the star and the forces acting upon it

---

#### properties of universe
* initialized at a drop zone
  * an area in the universe in which stars are spawned initially
---

