# Cheapest Flights Within K Stops: Bounded Bellman-Ford Explained

Cheapest Flights Within K Stops gives weighted directed edges and asks for the lowest price from src to dst using at most k stops. Plain Dijkstra is not enough, because the cheapest path might use too many stops.

The cleanest answer is Bellman-Ford limited to k + 1 rounds. Each round relaxes every edge once, and after round r the distance array holds the cheapest cost using at most r edges.

The trap: relax from a copy of the previous round's distances, not the array you are updating. Otherwise one round can chain several edges and silently break the stop limit.

Complexity is O(k * E) time and O(V) space, which is easy to justify given the constraints usually stated.

An alternative is Dijkstra over states (node, stops used). It works, but you must not discard a node just because it was visited with a lower cost, since a path with fewer stops can still matter. Mentioning this trade-off is a strong signal.

BFS by levels with pruning is a third option. Pick one, state why, and walk through a three-node example where the direct flight is expensive and the one-stop route is cheap.

Disclosure: I work on Linkjob AI. If you want to rehearse explaining problems like this with live hints, try [www.linkjob.ai](https://www.linkjob.ai/).
