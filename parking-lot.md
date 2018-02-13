### Parking Lot
Jimmy has a Parking Lot and wants to create a simple software to ease out his daily tasks. So here's what you got from his memo:

*"My parking lot has multiple levels and each level has multiple parking spots. We have at least 10 different sizes (0..9) of parking spots. So whenever a vehicle comes in, I'd like to assign this vehicle to the first level that has an available parking spot that can fit in the vehicle."*

You are required to:

1) Create a set of classes to manage this software.
2) Create a function `find_parking_spot` that returns the first parking spot in which an incoming vehicle can park.
3) Now Jimmy says that there are times in the day when more than one vehicle arrives at the gate of the parking lot. He also has a special parking spot where he can fit in multiple vehicles of different sizes, the only constraint is that the sum of car sizes to be parked in this special parking spot cannot be larger than 50. On the other hand, he charges a different price/hour depending on the brand of the vehicle. So Jimmy wants a way to determine the best combination of vehicles to fit in this special parking spot. 
So if Jimmy gets the following cars to be checked in:

 | Brand     |  Size | Price |
 | --------- |:-----:|:-----:| 
 | Dodge     |  15   | 50    |
 | Jaguar    |  20   | 170   |
 | Mercedes  |  10   | 100   |
 | Audi      |  20   | 30    |

Then he would let in the Dodge, the Mercedes and the Audi making a total profit of 180 and a total space consumption of 45 out of 50
