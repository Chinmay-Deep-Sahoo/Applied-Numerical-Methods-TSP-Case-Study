# TSP Case Study of Raipur Tourist Spots
<h2><b>Case Study Introduction:</b></h2>
<h4>We have considered 19 famous places for tourists to stop by when they visit Raipur, Chhattisgarh, India. We assumed some presumption which are listed below, to make the case study easier as this was a short duration project included in my coursework:</h4>
<ol>
<li>The tourists will reach Raipur at Raipur Airport, visit all 19 locations and then end the tour at Raipur Airport so that they can leave happily!!!!</li>
<li>We only consider minimizizing the traveling cost, we dont consider hotel or restraunt charges which might be cheaper near some places and expenisive near others</li>
<li>We consider travelling cost between point A to point B to be equal to the travelling cost between point B to point A, cost(A,B) = cost(B,A).</li>
<li>We don't consider the traveling prices to vary with time of the day, in other word we consider that at 6 AM and at 10 PM the cost between two points remains the same.</li>
</ol>
Provided all these assumptions we want to find the path which minimzes the total travelling cost such that the tourist starting at Raipur Airport visits all the 19 locations one at a time and then ends at Raipur Airport. To acheice this result we have used two techniques "<b>Mathematical Modelling of an IPP</b>" and "<b>Christofides Algorithm</b>". 

<h2><b>Mathematical Model:</b></h2>

<h4>Defining the mathematical model:</h4>
We define a mathematical function which is to be minimized to find the minimum cost and the optimum path, we start with a fully connected graph with edge weights as the cost of travelling between the two points. For each edge we define two binary variables which signify the choice of taking the edge or not. For example consider the edge joining the points 1 & 2, we will have two variables x<sub>12</sub> and x<sub>21</sub>, x<sub>12</sub> will tell whether we take the road from 1 to 2 and x<sub>21</sub> will tell whether we take the road from 2 to 1. We define Z, the total cost of traveling, as sum of edge weights multiplied by descision variables (eg: 45x<sub>12</sub> + 45x<sub>21</sub> + ....). Appart from this we have to define some constraints for the descision variables which are mentioned in the "Presentation.pdf" file. I recommend going through the presentation for better understanding of the mathematical model.

<h4>Solving the mathematical model:</h4>
Since the variables aren't continous over the space of real numbers we cant use any regular optimization techniques like Simplex, gradient descent, etc. We used the <b>brute force technique</b> to find the minimum value of Z, we searched through all possible combinations of all the binary variables and found the ones which follow all the constraints, amongst these solutions then we calculated the solutions which minimizes Z.

<h4>Limitations of this technique:</h4>
Though this method guarantees the optimum solution every time, it takes infeasible time to run the algorithm when the number of nodes are high (>5). The number of constraints increase exponentialy with increase in the number of nodes of the graph,
<center>
<div>
<img src="https://i.postimg.cc/8c6YmXML/Plot-1.jpg" width="1500"/>
</div>
</center>
and also the possible combinations of 1's and 0's increase exponentialy with number of nodes. We will have to check all these possible combinations in a loop, if we consider only 20 points as in our case, it would take around 10<sup>8</sup> years to look through all the possible combinations which is clearly not feasible.
<center>
<div>
<img src="https://i.postimg.cc/9FBbHjmr/Number-of-possible-solutions.jpg" width="1500"/>
</div>
</center>
