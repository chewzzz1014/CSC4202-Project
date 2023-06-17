# 6.0 Algorithm Specification

1.  Problem Definition:

    * Geographical Setting: Food delivery industry, covering urban and suburban areas.
    * Importance of AAD: AAD is crucial for optimizing delivery routes and delivery order assignment, minimizing delays, and ensuring food arrives in optimal condition.
    * Goal: Provide exceptional service to customers by minimizing delivery distance and ensuring food quality, thus enhancing customer satisfaction and loyalty.
    * Expected Output: Optimal delivery routes and order assignments that result in efficient and timely deliveries, preserving food quality.


2.  Development of a Model:

    * Data Type: Inputs include restaurant locations, delivery locations, food orders with descriptions and quantities, delivery time windows, and real-time traffic updates.
    * Objective Function: Minimize the total distance travelled, considering time constraints, food contents, and delivery windows.
    * Constraints: Time windows for deliveries, capacity constraints for drivers, and real-time traffic conditions.


3. Specification of Dijkstra's Algorithm:
   * Topic: Shortest Path Algorithm
   * Algorithm: Dijkstra's Algorithm
   * Rationale: Dijkstra's algorithm is a suitable choice for finding the shortest paths in a graph. In the context of food delivery, it can be used to optimize the delivery routes by finding the most efficient paths from restaurants to customers, considering factors like distance, delivery time windows, and traffic conditions.
   *   Comparison of Other Options:

       1. Greedy Algorithms & Graph Algorithm: While Dijkstra's algorithm can be both greedy algorithm and graph algorithm, it is specifically designed for finding the shortest paths while considering the food condition, therefore it is well-suited for this problem.
       2. Other shortest path algorithms like Bellman-Ford and Floyd-Warshall can also be considered, but Dijkstra's algorithm is chosen due to its efficiency in finding the shortest path from a single source node to all other nodes in a weighted graph.


4. Designing the Dijkstra's Algorithm:

&#x20;     The pseudocode for the optimized algorithm had been specified in the [previous section](../part\_2\_algorithm\_design/5\_algorithm\_design/5.3\_best\_travelling\_route.md).

5. Checking the Correctness of the Algorithm:

&#x20;        Perform asymptotic analysis and recurrence relations to ensure the correctness of Dijkstra's algorithm.

6. Analysis of the Algorithm:

&#x20;     Analyze the worst-case, best-case, and average-case time complexity and space complexity of the algorithm to evaluate its efficiency and scalability.

7. Implementation of the Algorithm

&#x20;      Choose a programming language of your preference (e.g., Python, Java) and implement Dijkstra's algorithm according to the designed specification.

7. Program Testing:

* Develop a testing strategy to verify the correctness and effectiveness of the implemented algorithm. Test the algorithm against various scenarios, including different delivery orders, time windows, and traffic conditions. Validate that the algorithm produces optimized delivery routes.

9. Documentation through Online Portfolio:

* Document the algorithm specification, including problem definition, input-output requirements, algorithm design, analysis, implementation details, and testing results. Maintain an organized online portfolio or documentation to ensure clarity and accessibility.
