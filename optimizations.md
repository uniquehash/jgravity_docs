# possible optimizations

### multi-threading
Obviously a single threaded program will take more time to complete then a multi-threaded program. Creating an algorithm that can calculate our values concurrently is no simple task, and will require a fair amount of experimentation to get down.

### multi-server
Multiple computers working the program will obviously process everything faster, so long as the overhead is proportional to the processing power gained. This goes beyond designing an algorithm that can run concurrently. We must also build a system to transfer information to multiple computer, store it in some capacity, manage the allocation of information between computers, and re-assemble it back together in a location.

### feature scaling
In our physics we can do something called feature scaling where we scale down our masses and distance by equivilent degrees to have to have the same proportional impact they normally would, but do so with smaller values. This would save us a bunch of headache with dealing with **big numbers** in terms of storage, processing, and rendering. A large part of this process would entail researching how to scale down our values (mainly mass and distance) while keeping the same proportional impact we would expect in a unscaled model.

