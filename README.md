<h1>Transportation Cost Analysis</h1>

<h2>Description</h2>
This academic project analyses the transportation problem faced by Exeter Transport Company (fictional), aiming to determine the optimal shipping strategy to minimise transportation costs. Various methods are tested, including heuristic approaches and a linear programming (LP) model on Excel, to compare efficiency and cost-effectiveness.



[Analysis on Excel](https://github.com/jordanbolling/Transportation-Cost-Analysis-Using-Excel/blob/main/Transport%20Excel.xlsx)



<h2>Utilities Used</h2>

- Excel (Mathematical operations, Linear Programming)
- Manual computation
  

<h2>Program walk-through:</h2>

Exeter Transport Company’s scenario is a minimum cost network flow problem. There are many methods to solve it, and each would yield different results. It is important to test each method and compare the results to find the optimal solution. The various methodologies can be seen below.

<p align="center">
Supply-Demand Network Diagram: <br/>
<img src="https://i.ibb.co/zWbB541G/Screenshot-2025-12-13-at-11-47-52.png"/>
</p>


The following visualises Exeter Transport Company’s shipping scheme.

This visualising technique displays their plan simply and clearly. Here, the ovals represent the nodes (geographical locations), and the arrows represent the nodes (shipping route). Additionally, the upper capacity limits have demand and supply of the mills and silos respectively are given on either side. To develop a model, this diagram can be built on through a tableau.
Transportation Tableau


<p align="center">
Below is the corresponding tableau generated <br/>
<img src="https://i.ibb.co/F4y4crGC/Screenshot-2025-12-13-at-11-48-08.png"/>
</p>


To simplify, the names of silos and mills have now been ignored but will be highlighted later. Each box here represents a unit transportation cost, and the corresponding supply and demand related to that cost are on either axis of the matrix. 
This tableau is crucial as allows for computation of basic feasible solutions (BFS).  
The feasible solutions that will be computed below are a set of non-negative values that fulfill the constraints, and the optimal solution illustrates the minimum total transportation cost.
Here demand and supply are considered as the constraints of the model, and this illustrates that this is a balanced transportation problem as total demand equals total supply.



**Identifying BFS**

The following are 3 methods of doing so. 


*Northwest Corner Method*

The following is a handwritten computation of the northwest corner method.

<p align="center">
Below is the corresponding tableau generated <br/>
<img src="https://i.ibb.co/ZRwXTz8p/Screenshot-2025-12-13-at-12-00-19.png"/>
</p>



As seen above, this method a developed from the transportation tableau. As this is balanced problem, no dummy rows or columns were necessary. The unit cost of 10 is in the northwest corner of matrix and therefore, that is the first allocation of the process. The corresponding demand limit is 5. Due to this, the appropriate supply capacity is only reduced to 10 from 15. A capacity of 5 is then allocated to this unit cost. Once the supply or demand of respective rows or columns have been limited to 0, it is crossed out. The procedure is continued until full cost allocation and the subsequent allocation is a unit cost of 2 with a capacity of 10, 7 with 5, 20 with 5, 9 with 15 and finally 18 with an allocation of 10 is left.

This produces the following result.10(5) + 2(10) + 7(5) + 9(15) + 20(5) + 18(10) = 610. Therefore, the total transportation cost is $61000.

This is the simplest method and produces a BFS the quickest out of the next few procedures. 

Below is the least cost method, which is widely considered as an optimal method for finding a BFS.



*Least-Cost Method*

The figure below is a handwritten computation of this method.

<p align="center">
Below is the corresponding tableau generated <br/>
<img src="https://i.ibb.co/sJCBxsqR/Screenshot-2025-12-13-at-12-00-42.png"/>
</p>



There were a few important steps in this process. The minimum costs were allocated in this order: 2 with a capacity of 15 allocated to it and the corresponding row and column were crossed out as they both had a value of 15. Subsequently, 4 with a capacity of 5, 9 with 15, 18 with 5 and finally 20 with a capacity remained.  
This produces the following result. 2(15) + 4(5) + 9(15) + 18(5) + 20(10) = 475. Therefore, the total transportation cost is $47500.
Although the Northwest method produces an initial BFS easily, this method produces a lower cost solution.



*Vogel’s Method*

It achieved through the following handwritten computation.

<p align="center">
Below is the corresponding tableau generated <br/>
<img src="https://i.ibb.co/sLkmjck/Screenshot-2025-12-13-at-12-01-03.png"/>
</p>



This process shares similarities with the minimum cost method. Here, row and column penalties are computed and the minimum cost of row or column with the lowest penalty is identified, and similar procedure is followed as the previous method. Here, firstly a cost 2 is pinpointed out and a capacity of 15 is allocated to it. Then 4 with 5, 9 with 15, 18 with 5 and finally 20 with 10. 

This produces the following result 4(5) + 2(15) + 9(15) + 18(5) + 20(10) = 475. Therefore, the total transportation cost is $47500.

This procedure for finding the BFS tries to avoid extremely high shipping costs. 

For a more comprehensive solution to the problem, a mathematical model of the Exeter Transport Company scenario would be the best approach.




**Mathematical Model**

This problem can be formulated as linear programming model with the objective of minimizing the total transportation cost because it follows a similar structure to the previous project. A linear equation can be constructed from the minimization objective with decision variables, an objective function, constraints which can be written as linear inequalities or equations (‘Superprof’,2019). This is shown below.

Decision Variables


<p align="center">
Below is the corresponding tableau generated <br/>
<img src="https://i.ibb.co/678YJLnC/Screenshot-2025-12-13-at-12-01-36.png"/>
</p>



This can be used to produce the following objective function.


Objective Function

Minimize C = 10X1 + 12X2 + 4X3 + 2X4 + 7X5 + 14X6 + 20X7 + 9X8 + 16X9 + 11X10 + 20X11 + 18X12

Subject to,

Demand Constraints:
X1 + X2 + X3 >= 5
X4 + X5 + X6 >= 15
X7+ X8 + X9 >= 15
X10 + X11 + X12 >= 15

Supply Constraints:
X1 + X4 + X7 + X10 <= 15
X2+ X5+ X8 + X11 <= 25
X3+ X6 + X9 + X12 <= 10



Using spreadsheeting modelling, the following has been computed.


<p align="center">
Linear Programming Used: <br/>
<img src="https://i.ibb.co/VrJCYGG/Screenshot-2025-12-13-at-11-49-07.png"/>
<br/>
Solver Parameters Set: <br/>
<img src="https://i.ibb.co/5W1FTv6M/Screenshot-2025-12-13-at-12-02-04.png"/>
</p>



This has produced 435 as its result. Therefore, the total transportation cost here is $43500.



**Conclusion**

The LP model has produced the result with the lowest total cost. The least-cost and Vogel’s method produced the same result as they essentially followed the same allocation. Despite the convenience of the northwest corner method, its total cost was significantly higher. Therefore, the mathematical method is optimal for this problem.


**Recommendations**

•	The $4000 difference between the heuristic approaches (least-cost and Vogel’s) isn’t significant and should therefore be used when a quick and easy result is needed.
•	Although, the minimization of transportation cost is a crucial goal for the Exeter Transport Company, measures taken to be more sustainable, ensure delivery time goals are met and balancing customer satisfaction are other critical goals which mustn’t be ignored, especially with increased need for businesses to be more sustainable.
•	It is also important to not disregard other processes such as northwest corner method because transportation costs tend to fluctuate and can often be volatile. Therefore, having many angles of looking at an issue is always useful. It can therefore be recommended that although an LP approach should be prioritized, resources should also be spent in finding a BFS using each of the above methods.
