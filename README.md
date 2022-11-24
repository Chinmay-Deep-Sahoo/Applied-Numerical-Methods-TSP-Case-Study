# TSP Case Study of Raipur Tourist Spots
<h2><b>Case Study Introduction:</b></h2>
<h4>We have considered 19 famous places for tourists to stop by when they visit Raipur, Chhattisgarh, India. We assumed some presumptions which are listed below, to make the case study easier as this was a short duration project included in my coursework:</h4>
<ol>
<li>The tourists will reach Raipur at Raipur Airport, visit all 19 locations and then end the tour at Raipur Airport so that they can leave happily!!!!</li>
<li>We only consider minimizing the traveling cost, we don't consider hotel or restaurant charges which might be cheaper near some places and expensive near others</li>
<li>We consider the traveling cost between point A to point B to be equal to the traveling cost between point B to point A, cost(A, B) = cost(B, A).</li>
<li>We don't consider the traveling prices to vary with the time of the day, in other words, we consider that at 6 AM and 10 PM the cost between the two points remains the same.</li>
</ol>
Provided all these assumptions we want to find the path which minimizes the total traveling cost such that the tour starts at Raipur Airport visits all 19 locations one at a time and then ends at Raipur Airport. To achieve this result we have used two techniques "<b>Mathematical Modelling of an IPP</b>" and "<b>Christofides Algorithm</b>". 

<h2><b>Mathematical Model:</b></h2>

<h4>Defining the mathematical model:</h4>
We define a mathematical function that is to be minimized to find the minimum cost and the optimum path, we start with a fully connected graph with edge weights as the cost of traveling between the two points. For each edge, we define two binary variables which signify the choice of taking the edge or not. For example, consider the edge joining points 1 & 2, we will have two variables x<sub>12</sub> and x<sub>21</sub>, x<sub>12</sub> will tell whether we take the road from 1 to 2, and x<sub>21</sub> will tell whether we take the road from 2 to 1. We define Z, the total cost of traveling, as the sum of edge weights multiplied by decision variables (eg: 45x<sub>12</sub> + 45x<sub>21</sub> + ....). Apart from this, we have to define some constraints for the decision variables which are mentioned in the "Presentation.pdf" file. I recommend going through the presentation for a better understanding of the framing of the mathematical model.

<h4>Solving the mathematical model:</h4>
Since the variables aren't continuous over the space of real numbers we can't use any regular optimization techniques like Simplex, gradient descent, etc. We used the <b>brute force technique</b> to find the minimum value of Z, we searched through all possible combinations of all the binary variables and found the ones which satisfy all the constraints, amongst these solutions, we calculated the solution that minimizes Z.

<h4>Limitations of this technique:</h4>
Though this method guarantees the optimum solution every time, it takes infeasible time to run the algorithm when the number of nodes is high (>5). The number of constraints increases exponentially with an increase in the number of nodes of the graph,
<center>
<div>
<img src="https://i.postimg.cc/8c6YmXML/Plot-1.jpg" width="1500"/>
</div>
</center>
and also the possible combinations of 1's and 0's increase exponentially with the number of nodes. We will have to check all these possible combinations in a loop, if we consider only 20 points as in our case, it would take around 10<sup>8</sup> years to look through all the possible combinations which is clearly not feasible.
<center>
<div>
<img src="https://i.postimg.cc/9FBbHjmr/Number-of-possible-solutions.jpg" width="1500"/>
</div>
</center>

<h2><b>Christofides Algorithm:</b></h2>
This is a famous algorithm that is used to solve the TSP problem, this algorithm is based on the greedy approach. Without using any mathematical model to optimize, it directly works on the graph network to find the optimum path. For a  better understanding of this algorithm, I recommend going through a YouTube video which is linked in the reference section of this case study.<br><br>
There are 6 steps to this algorithm starting from the fully connected graph, full working of each step is out of the scope of this case study, for more information you may read further on each step on your own, (though I have provided the codes for reference).
<ol>
<li>Make the minimum spanning tree from the fully connected graph.</li>
<li>Isolate the nodes that have an odd degree from the minimum spanning tree.</li>
<li>Get the minimum cost perfect matching of all these odd degree nodes.</li>
<li>Make an Eulerian graph by adding the two graphs from steps 1 & 3.</li>
<li>Find the Eulerian cycle from this eulerian graph.</li>
<li>Remove repeated nodes to finally get the optimum path.</li>
</ol>

<h4>Limitations of this technique:</h4>
This algorithm works very fast and is practically usable in our case study but this is a greedy approach so it doesn't guarantee the optimum path. This algorithm has an error margin of 50%. So if we get an optimum cost of ₹100 from the Christofides Algorithm we can be sure that there doesn't exist any path which costs less than ₹50.

<h2><b>Results:</b></h2>
Since the mathematical model is not possible due to its time constraint we can't use that algorithm for our 20 nodes graph, as in our case study. We used Christofides Algorithm to get the results of our case study. The results are present in the "Presentation.pdf", the data used and the codes are provided in this repository, and people are welcome to download them and play with them.

<h2><b>References:</b></h2>
References are mentioned at the end of "Presentation.pdf".
