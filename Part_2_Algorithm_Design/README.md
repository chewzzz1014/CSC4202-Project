# Part 2 - Algorithm Design

## 4.0 Model Development of Scenario
### 4.1 Overview

The optimized delivery route algorithm focuses on efficiently determining delivery prioritization of food orders to multiple destinations and the best routes for deliveries. This becomes particularly significant when drivers receive multiple orders simultaneously from the same restaurant, convenience store or shop. The determination of the best route is based on a combination of two factors: the distance to be covered and the priority level of the food being delivered.  

The scenario can be divided into two main components: 
 1.	Determine the delivery prioritization of multiple food orders.
 2. Identify the best route to travel according to the determined delivery prioritization that considers distance and food quality factors.

### 4.2 Delivery Prioritization for Food Orders
For determining the delivery prioritization of food order, there are 2 possibilities. At any time, the drivers only receive 1 food order from the restaurant, so they can proceed to deliver that food order. When drivers are tasked with multiple food orders with different destinations at the same time, determining the delivery prioritization becomes more complex. In such cases, it is necessary to establish a systematic approach to prioritize and sequence the delivery of these food orders. Distance of the food order destination and food contents of the food order are considered for determining such delivery order.

Firstly, distance is the primary consideration when it comes to sequencing delivery order. The prioritization of food orders is primarily based on the distance between the starting point (typically the restaurant or shop) and the destination of each food order. The focus is on identifying the food order with the shortest traveling distance from the restaurant, regardless of the presence of a direct route between them. This approach allows for the efficient selection of the nearest food order destination, ensuring that deliveries can be made in a timely manner. 

The food contents of the food order are the secondary consideration when to comes to sequencing delivery order. The remaining shelf life of the food items is considered in determining delivery prioritization, where food items having a shorter remaining shelf life are being prioritized. For example, cold coffee is prioritized over fried chicken, and ice cream is prioritized over cold coffee. Priority values, ranging from 0 to 1, are assigned to each food category based on the remaining shelf life, indicating the level of attention required when determining the delivery prioritization.
 
However, the scenario can become more complex in certain cases. When the driver receives multiple food orders with the exact same combinations of food items, the food contents factor does not play a role in prioritization. In such cases, distance becomes the sole factor affecting the delivery prioritization. This raises the challenge of finding the right balance between distance and food contents factors. In addition, how to determine the prioritization if a food order consists of food items of different food categories, each with different priority value?
 
To address these challenges, a weight formula is used to calculate the weight value of food orders. Each food order is assigned a weight value that takes account of both the distance and priority value of the food items. The weight value is a reflection of the importance and prioritization of the food order. The food order with the lowest weight value will be delivered first, followed by the remaining food orders in ascending order of their weight value.
 
If all food orders contain the exact same combinations of food items, the priority value for all food items is assumed to be 0, and the weight value depends solely on the distance factor. On the other hand, if a food order consists of multiple food categories with different priority values, the maximum priority value among them is used to calculate the weight value of a food order. This approach ensures that the food item with the highest priority value in a food order is efficiently considered when determining the overall priority of the food order. In certain cases, the priority value of the food items can outweigh the distance factor, particularly when there are significant differences in the priority values between food orders. This will be further elaborated in the subsequent section.

### 4.3 Best Travelling Route

Once the delivery prioritization of all food orders has been determined, the next step is to find the best travelling route based on this determined delivery order. When travelling from one destination to the next destination, the path with shortest distance must be chosen to minimize the time taken for completing the food orders. This means that there is a need to keep track of the distances between food order destinations. By maintaining the distance information for each possible path connecting the destinations, it becomes possible to compare and evaluate the different routes. The diagram below displays the representation of the scenario in the form of a weighted graph. The detailed implementation of this algorithm will be discussed in the subsequent section.

![image](https://github.com/chewzzz1014/CSC4202-Project/assets/92832451/23d94ffe-e94a-4ce8-a832-621cb36ba7e9)


### 4.4 Constraints and Challenges

One of the most significant challenges of this optimization is to efficiently categories food items based on their respective food categories. This process is particularly important as it will affect the delivery prioritization for food orders, especially when all food orders have a similar distance from the restaurant. 

In our optimized algorithm, there are 3 main food categories: cooked food, cold/hot drink and dessert. However, it's important to note that not all food items fall strictly under these categories, and there may be cases where certain food items require special attention. For instance, a customer may specifically request their noodle soup to remain warm by the time they receive it. Such special conditions or requirements for food items are not explicitly covered by the optimized algorithm.

On the other hand, this optimized algorithm does not guarantee the perfect balance between distance and food contents factors. While delivery optimization is taken care of, the resulting delivery order may not always correspond to the shortest route for traveling between destinations. In some cases, there may be alternative routes that could potentially be shorter or faster than the one suggested by the optimization algorithm.


## 5.0 Algorithm Design
### 5.1 Overview

The optimized delivery route algorithm consists of two main parts: determining the delivery prioritization of food orders and finding the best travelling route based on these orders. Delivery prioritization is carried out considering distance and food item priority. The second part involves implementing the Dijkstra algorithm to find the best route based on the determined delivery prioritization. 

The scenario is assumed to be a graph problem. The nodes of graph represent starting point and deliveries destinations; the edges between nodes represent the travelling paths between 2 places. If an edge connects between starting point and delivery destination, this edge is labelled with food order’s weight value that is calculated using a specific weight formula which takes account of both distance and food quality factors. Else, if an edge connects two destinations, then the weight is just the distance of the path between these destinations. The weight value is crucial for determining the delivery prioritization, and what are the most efficient travelling paths for completing all food orders. It’s worth noting that that is no guarantee that there is a direct path between starting point and a destination. If there is such a case, the shortest distance between them will be used for calculating the weight value. Below summarizes the important points for representing the scenario in graph form:

1. Node represents the starting point and delivery destinations.
2. Edge represents the travelling path.
3. If there’s a connected path (edge) between starting point and destination, the distance of path is used to calculate food order’s weight value. Label the edge with this weight value.
4. If there’s a connected path between destinations, label this edge with the distance of path.
5. Else if there’s no direct path between the starting point and destination, the distance used for calculating weight value is the distance on map.

The Dijkstra algorithm is used to determine the best route starting from food order destination with lowest weight value and continuing to subsequent destinations while ensuring optimal efficiency and customer satisfaction. 

### 5.2 Delivery Prioritization for Food Orders

At any time, if the driver only receives one food order from the restaurant, then he/she can proceed to complete the order. However, if the driver receives multiple food orders at the same time, the weight value of the food order plays an important role in determining the best delivery route. The delivery should start with the order destination with lowest weight value. The weight value is calculated using the formula

![image](https://github.com/chewzzz1014/CSC4202-Project/assets/92832451/ab49bbde-e64b-4f31-b680-d9d87819d55e)

Each food item will be assigned a priority value based on its respective category. The priority value ranges between 0 and 1. The priority value is determined by the remaining shelf life of the food item, where a shorter shelf life corresponds to a higher priority value. A higher priority value indicates that the food item should be prioritized during the delivery process. 

The distance factor is given primary consideration in the weight calculation as it covers other secondary costs such as fuel cost and overall efficiency. However, there are scenarios where food quality becomes more significant. This occurs when multiple food orders have similar traveling distances and different combinations of food items. In such cases, the food order with a higher priority value, indicating shorter remaining shelf life, will be prioritized and delivered first. By balancing the weight calculation between distance and priority value, the algorithm ensures optimal delivery decisions that account for both efficiency and customer satisfaction.

The following are the food categories along with their associated priority values:

Food Category|Priority Value
|---|---|
Cooked Food|0.3
Cold / Hot Drinks|0.5
Dessert|0.8

If the driver receives multiple food orders containing the exact same combination of food items, the priority value for all food items in all food orders is assumed to be 0. Therefore, the weight value solely depends on the distance from the destinations since no food item takes priority over another. Conversely, if the combination of food items differs for each food order, every food item in every order will be assigned a priority value. The maximum priority value among the food items in an order is then selected as the food order's priority value for calculating their respective weight values. The delivery process starts with the food order with lowest weight value and follows by other food orders in ascending weight value. Below summarized the process for determining the delivery prioritization:

1.	If the driver receives a single food order, proceed with delivering that order.
2.	If the driver receives multiple food orders with identical combination of food items, assume all food items have a priority value of 0, proceed to step 5.
3.	If each order consists of a different combination of food items, proceed to step 4.
4.	For every order, assign a priority value to each food item. Select the maximum priority value among food items as the food order's priority value. 
5.	Calculate the weight value for each food order using the provided formula.
6.	Start delivering the food order with the lowest weight value, followed by other food orders in ascending weight value.


### 5.3 Best Travelling Route 

After determining the delivery prioritization, the Dijkstra algorithm will be used to find the optimal route. As the driver moves from one destination to the next destination following the determined delivery prioritization, they must choose the path with the shortest distance to the subsequent destination. In this context, the edges connecting between destinations have the weight value representing the traveling distance. Therefore, when travelling from one destination to the next, the driver should select the path with the lowest weight value, as it signifies the shortest distance. By adhering to this approach, the driver can efficiently navigate the delivery route while minimizing travel distances and ensuring timely deliveries.

The Dijkstra algorithm can determine the best route with minimal weight. Below listed the pseudocode of implementing Dijkstra:

```
1. Create an empty set called "visited" to keep track of the visited nodes.

2. Create a list called "weights" to store the weights from the starting point to each destination. Initialize all weights to infinity except for the starting point, which is set to 0.

3. Create a list called "destinations" to store the destinations to be visited in determined delivery prioritization.

4. While there are unvisited destinations:
     4.1. Choose the next destination from the "destinations" list, which is not already visited. Let's call this destination "current".
     4.2  Add "current" to the "visited" set.
     4.3  For each neighbor of "current" that is not in the "visited" set:
           4.3.1 Calculate the tentative weight from the starting point to the neighbor through "current". This weight is the sum of the weight from the edges from starting point to "current" and the neighbor.
           4.3.2 If the tentative weight is less than the current weight stored in the "weights" list for the neighbor, update the weights to the tentative weight.
        
5.	Return the "weights" list, which now contains the best route from the starting point to each destination, following the determined delivery order.
```

![image](https://github.com/chewzzz1014/CSC4202-Project/assets/92832451/452f3d43-a3c4-4f10-91e7-bc67bbfd0f55)

The above figure displays an example of the representation of the scenario in the form of a weighted graph. Since Dijkstra algorithm always prefer path with lower weight, there is a need to identify weight of all edges using the following algorithm:

1. The edge connects starting point and food order destination. The edge is labelled with weight value of the food order.
2. The edge connects different destinations. The edge is labelled with the distance as its weight.
3. No edge (path) connects starting point and food order destination. However, the weight formula requires distance value. Thus, take the shortest distance of unconnected path between them to be used in weigh value calculation.

After assigning weights to all edges in the graph, the next step is to determine the best route using the Dijkstra algorithm. This algorithm will calculate the shortest path from the starting point to each destination in the determined delivery order. When traveling from one destination to the next, the driver should always choose the shortest path possible. This means selecting the edge with the lowest weight, which represents the shortest distance between two destinations. The detailed scenario background of this graph and algorithm steps will be discussed in the following section.

### 5.4 Example

David, a food delivery driver, has received 3 orders from the same restaurant at the same time. Here are the details for these orders:

![image](https://github.com/chewzzz1014/CSC4202-Project/assets/92832451/82b8d9b1-06b0-47b0-9889-0fdb9fb10f3f)


Using the current implementation of delivery route planning algorithm, the order with closest distance will be delivered first. In this example, order 2 will be delivered first, followed by order 1 and order 3. However, by the time the customer of order 1 receives his food, the ice cream will be melted. Same goes to customer order 3 who will receive her warm Latte. This is why the optimized delivery route algorithm is required for ensuring user satisfaction.

Since David receives multiple orders with different combinations of food items at the same time, the priority value for each food item must be determined for calculating the weight value of orders. Priority value is assigned to food items based on their respective categories. Table below categories food items into 3 main categories.

![image](https://github.com/chewzzz1014/CSC4202-Project/assets/92832451/703ce078-3cb1-4544-963e-9c0b01fb35fd)

To determine the priority value for an order, consider the maximum priority value among its food items. This ensures that the order with the most "urgent" food items will always be prioritized. In the given example, Order 1 will be assigned a priority value of 0.8, Order 2 will have a priority value of 0.3, and Order 3 will have a priority value of 0.5. Subsequently, the weight value for each order can be calculated using the defined weight formula, taking into account both the distance and priority value factors.

![image](https://github.com/chewzzz1014/CSC4202-Project/assets/92832451/dfb1c6c8-03e9-4f3b-8b37-bfbc4be0b3a2)


Based on the weight values obtained, the delivery prioritization will be as follows: Order 1 will be delivered first, followed by Order 2, and finally Order 3. This sequence is determined by considering both the distance and priority value factors.
 
In the case of Order 3, it is delivered last due to the longer traveling distance compared to the other orders. However, for Order 1 and Order 2, the priority value outweighs the distance factor since the difference in priority values is significant. Order 1 consists of several desserts with a short remaining shelf life that indicate their urgency. Therefore, they need to be delivered to the customer promptly, prioritizing food quality over distance. 

After determining the delivery prioritization, Dijkstra algorithm is used to find the best delivery route.

![image](https://github.com/chewzzz1014/CSC4202-Project/assets/92832451/26f0193e-b92c-4f93-be58-fb4c644b71f5)


Destination = {restaurant, order 1, order 2, order 3}
|Visited|Current|W[Order 1]|W[Order 2]|W[Order 3]
|---|---|---|---|---|
|Restaurant|-|Infinity|Infinity|7
Restaurant, Order 1|	Order 1	|12	|9	|7
Restaurant, Order 1, Order 2|	Order 2|12|	9	|7
Restaurant, Order 1, Order 2, Order 3|Order 3|12|9|	7



The table above lists the steps of determining the shortest possible route to each destination while delivering the food order follows the determined prioritization order. Therefore, David will need to travel in such a way

1.	[Restaurant -> destination order 3 -> destination order 1]: for delivering order 1
2.	[destination order 1 -> destination order 2]: for delivering order 2
3.	[destination order 2 -> destination order 1 -> destination order 3]: for delivering order 3

The total weight of the overall travel is the sum of the weights of each individual travel. In this case, the weight of the first travel is 12, the weight of the second travel is 4, and the weight of the third travel is 9. Therefore, the total weight of the overall travel is 25.
