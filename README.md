# Dynamic-Programming

A program that will him to lift 1000kg. We has several (positive integers 
less or equal than 1000) weight plates, possibly of different weights, and its goal is to add some
of the plates to a bar so that it can train with a weight as close as possible to 1000kg. Given the 
(possible) case where two numbers are equally close to 1000 (e.g.,995 and 1005), we will pick the greater one (in this case 1005).
WE will need to complete the function weight, which receives as a parameter a list of positive integers (where each integer is less than
or equal than 1000), denoting the weight of each plate. You can safely assume that the length of
the list is between 1 and 1000. The function must return one integer, the combined weight closest
to 1000.
