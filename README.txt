Collaborator: Danny Rose

1.  The mips code is taking an array and first adding all the values
smaller than the average to the buffer pointer, and then adding all the
values greater than the average afterwards. It then calls itself recursively
first on the smaller values and then on the larger values, increasing the buffer
pointer by 20 words each time to not override anything. Essentially, the buffer is
simply used as storage for the arrays created, and the code keeps track of the 
buffer pointer on the stack and preserves it so that it can be used to indicate the
start of the array being passed into the function. The rest of the function (printing,
calculating average, etc.) works the same as in c++.

2.  In general, changing the depth will increase the space allocated on the stack because it will
result in more recursive calls which allocate more space each time. Also generally, changing
the size of the array doesn't affect the space allocated on the stack because the depth
is more deterministic of how many recursive calls will occur. However, if the array is small
enough relative to the depth so that the condition (length == 1) is reached before (depth == 0),
then increasing the size of the array by enough to change which end condition is reached first
will increase the space allocated on the stack, and the reverse is true as well. Also in this
case, changing depth will have no effect unless it also changes the end condition that is
reached first. 