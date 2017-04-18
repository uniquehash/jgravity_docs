# formulas

delta_t = step of time to use


* const_distance = `sqrt(pow(xA - xB, 2) + pow(yA - yB, 2) + pow(zA - zB, 2))`
  * https://math.stackexchange.com/questions/42640/calculate-distance-in-3d-space

* force
  * fX = `(massB * (6.673 * pow(10, -11) / pow(const_distance, 3)) * (xB - xA))`
  * fY = `(massB * (6.673 * pow(10, -11) / pow(const_distance, 3)) * (yB - yA))`
  * fZ = `(massB * (6.673 * pow(10, -11) / pow(const_distance, 3)) * (zB - zA))`

* const_force = `(massB * (6.673 * pow(10, -11)) / pow(const_distance, 3))`

* delta_velocity
  * delta_vX = `fX * delta_t`
  * delta_vY = `fY * delta_t`
  * delta_vZ = `fZ * delta_t`
  
* velocity
  * vX = `vX + delta_vX`
  * vY = `vY + delta_vY`
  * vZ = `vZ + delta_vZ`
  
* coordinates
  * delta_X = `vX * delta_t`
  * delta_Y = `vY * delta_t`
  * delta_Z = `vZ * delta_t`
  
* aggregating mass of forces acting on a star
  * sigma_mass = `i = 1 sigma (mass(i))`

* aggregating position for forces acting on a star
  * sigma_x = `(sigma x(i) * mass(i)) / sigma(mass(i))`
  * sigma_y = `(sigma y(i) * mass(i)) / sigma(mass(i))`
  * sigma_z = `(sigma z(i) * mass(i)) / sigma(mass(i))`
 
  
  
  
  
