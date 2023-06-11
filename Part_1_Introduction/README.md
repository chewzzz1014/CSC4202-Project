# Part 1 - Introduction
## 1.0 Scenario and Problem

Company Z is an ambitious startup in the competitive food delivery industry, aiming to prove itself as a formidable player and compete against the top food delivery platforms in the market. Like other platforms, Company Z's platform offers a convenient medium for restaurants and shops to showcase and sell their food products, while freelance drivers are engaged to handle the delivery during their free time. With a seamless user experience in mind, Company Z's platform provides user-friendly interfaces for smooth transactions, efficient delivery coordination, and clear delivery maps. Restaurants and shops can easily upload their food offerings, complete with descriptions, images, and pricing details. This allows customers to explore a diverse range of food options. Besides that, through an intuitive delivery map interface, drivers can efficiently navigate their assigned routes, optimizing time and distance. The map interface provides real-time updates, enabling drivers to monitor traffic conditions and keeps customers informed about the progress of their orders. Company Z offers food delivery services across a wide range of areas. Their coverage extends from urban areas to suburban areas. 

With a vision to supply exceptional service and a commitment to customer satisfaction, Company Z conducted detailed surveys and market research to understand the existing challenges faced by customers when using other food delivery platform services. Company Z found out that most of the customers are concerned about the state of food been delivered to them, especially the quality of food which has shorter remaining shelf life like ice cream and cold drinks. 
  
One of the significant challenges faced by customers on other food delivery platforms is dissatisfaction with the delivery service. A common issue arises when drivers handle multiple orders with varying distances from the restaurant or shop. In these cases, drivers often prioritize delivering the order to the nearest destination first. Their primary motivation is to complete all orders quickly and maximize their efficiency to accept more orders afterwards. Although this approach seems reasonable from the driver's perspective, many customers have complained about the quality of the delivered food. Customers have expressed frustration and dissatisfaction as their food arrives cold, melted, or spoiled due to the prioritization of distance and speed over food quality. According to one of the reviews left on the Company Z’s competitor, Company A's feedback portal, 'what is the purpose of fast delivery when you can't even deliver my ice cream cake intact?'. 

The impact of delayed delivery due to inefficient route planning is detrimental to both customer satisfaction and the reputation of the food delivery platform. Dissatisfied customers may share their negative experiences, resulting in a loss of trust and credibility for the platform. Moreover, the compromised quality of food items can lead to financial losses for the platform and dissatisfaction among restaurant partners.
 
To address this issue, Company Z recognizes the important role of algorithm analysis in optimizing delivery routes and delivery order assignment to the drivers. They aim to assign more efficient and cost-optimized routes to their drivers. The algorithm takes into account factors such as distance of path and food contents of food orders. Through intelligent analysis of these variables, the algorithm determines the delivery prioritization of food orders and efficient route for each delivery for enhancing overall operational efficiency.
 
The goal of Company Z in implementing this optimized algorithm is twofold. Firstly, they strive to provide exceptional service to customers by minimizing delivery distance and ensuring that food arrives in optimal condition. By assigning drivers to the most efficient routes, Company Z aims to enhance the overall customer experience and satisfaction. Secondly, by differentiating themselves from competitors through efficient delivery operations, Company Z aims to establish a strong reputation in the food delivery industry and gain a competitive edge in the market. Through the implementation of this optimized algorithm, Company Z aims to achieve customer loyalty, attract more restaurant partners, and position themselves as a top-tier food delivery platform that prioritizes efficiency, reliability, and customer satisfaction.


## 2.0 Importance of Optimal Solution

## 3.0 Algorithm Suitability Review


1.	**Sorting**
    1. Strengths
       - Sorting algorithms can be useful for optimizing the order of deliveries based on factors such as distance, delivery time windows, and food item sensitivity.
       - They can help prioritize deliveries to minimize the time taken and ensure that temperature-sensitive items are delivered promptly. Weaknesses:
       - Sorting alone may not be sufficient to address the problem comprehensively, as it primarily focuses on optimizing the order of deliveries but does not consider other factors like real-time monitoring, quality control, or customer feedback.


2.	**Divide and Conquer (DAC)** 
    1. Strengths
       - DAC algorithms can be applied to optimize the overall delivery process by breaking it down into smaller, manageable subproblems. 
       - It can help with route optimization, grouping deliveries based on location or specific food item requirements, and addressing specific challenges efficiently. Weaknesses:
       - DAC algorithms may not directly address the core issue of compromised food quality unless coupled with other strategies like real-time monitoring, quality control, or driver guidelines.


3.	**Dynamic Programming (DP)** 
    1. Strengths:
       - DP algorithms can be useful for optimizing decisions made during the delivery process.
       - It can help determine the most efficient routes, considering various factors like distance, delivery time windows, and food item sensitivity, to minimize overall delivery time and prioritize sensitive food items. 
    2. Weaknesses:
       - DP algorithms may have high computational complexity, especially when dealing with large-scale delivery networks and numerous constraints.
       - They may require extensive problem modeling and dynamic state transitions, which can be challenging to implement and maintain.


4.	**Greedy Algorithms**
    1. Strengths:
       - Greedy algorithms are simple and intuitive, making them easy to implement and understand.
       - They can be effective in certain scenarios, such as optimizing deliveries based on distance or minimizing delivery time. 
        Weaknesses:
       - Greedy algorithms may not always lead to an optimal solution since they make locally optimal choices without considering the global consequences.
       - They may overlook other important factors like food item sensitivity or real-time monitoring, which can affect the overall quality of delivered food.

5.	**Graph Algorithms** 
    1. Strengths:
       - Graph algorithms, such as Dijkstra's algorithm or A* search, can be applied to optimize the delivery routes and prioritize time-sensitive deliveries.
       - They can consider factors like distance, traffic conditions, and delivery time windows to minimize overall delivery time and maintain food quality. 
    2. Weaknesses:
       - Graph algorithms may require comprehensive network modeling and data representation, which can be complex and time-consuming to implement.
       - They may not directly address issues related to real-time monitoring, quality control, or customer feedback unless integrated with other strategies.

In conclusion, while sorting, DAC, DP, greedy, and graph algorithms have their strengths and weaknesses, it is important to note that addressing the problem of compromised food quality in food delivery platforms requires a holistic approach. Combining multiple strategies, including algorithmic optimizations, real-time monitoring, quality control measures, and customer feedback systems, would likely provide a more comprehensive solution to ensure the freshness and quality of delivered food.
