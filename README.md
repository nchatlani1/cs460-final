# The Torchbearer

**Student Name:** Nitin Chatlani
**Student ID:** 827870037
**Course:** CS 460 – Algorithms | Spring 2026

---

## Part 1: Problem Analysis

- **Why a single shortest-path run from S is not enough:**
  The single shortest-path run from S will provide the most effective distance from point a to point b but it doesn't consider any future distances that need to be traveled (and more importantly doesn't consider the final position that is visited). It helps with finding the path from start to a relic individually but won't work for getting through all relics in the least amount because it doesn't optimize total distance, just distance from one point to the next.

- **What decision remains after all inter-location costs are known:**
After all iter-location costs are known, we still need to figure out the best order to travel to each relic.
- **Why this requires a search over orders (one sentence):**
This requires a search over orders because we are optimizing total fuel which depends on the order of visits, which by nature, requires searching each one; ordering also could require a lot of unneccessary computation. 
---

## Part 2: Precomputation Design

### Part 2a: Source Selection

| Source Node Type | Why it is a source |
|---|---|
| Spawn Location | This is where the torchbearers journey begins so we must find the most inexpensive distance from them to each relic chamber and the exit |
| Relic Locations | Each time the torchbearer stops, it is at a relic chamber, so calculating the distance from other relics that we haven't been to yet and to the exit is needed. |

### Part 2b: Distance Storage

| Property | Your answer |
|---|---|
| Data structure name | Nested Dictionary|
| What the keys represent | Source node rep. outer, relic nodes rep. inner key|
| What the values represent | minimum fuel cost from point a to b |
| Lookup time complexity | O(1)|
| Why O(1) lookup is possible | Because we are utilizing hashmaps which have a key that can be accessed in O(1) time. |

### Part 2c: Precomputation Complexity

- **Number of Dijkstra runs:** k+1.
- **Cost per run:** _your O(mlogn)
- **Total complexity:** O((k+1) * mlogn) = O(k * mlogn) 
- **Justification (one line):** Every run hits each edge of the min-heap and each node also runs Dijkstras alg.
---

## Part 3: Algorithm Correctness

### Part 3a: What the Invariant Means

- **For nodes already finalized (in S):**
Finalized distances from the spawn to node.
- **For nodes not yet finalized (not in S):**
Current cheapest path from source using finalized nodes as waypoints.

### Part 3b: Why Each Phase Holds
> One to two bullets per phase. Maintenance must mention nonnegative edge weights.

- **Initialization : why the invariant holds before iteration 1:**
The invariant holds before interation 1 because the only known distance is from the source to the source (cost = 0), holds.
- **Maintenance : why finalizing the min-dist node is always correct:**
Finalizing the min-dist node is always correct becuase all of th edge weights are nonnegative so all of the future unfinalized paths would be able to provide a shorter path copmared to the node u (from min heap which contain shortest CURRENT distance known).
- **Termination : what the invariant guarantees when the algorithm ends:**
When the algorithm ends, the invariant guaruntees that all accessable nodes will be in S and have their shortest path possible.
### Part 3c: Why This Matters for the Route Planner

Distances in between the spawn and the exit that are miscalculated could land the torchbearer in a relic chamber that is not actually as cheap as it seems, therefore using more torch fuel than expected meaning the torchbearers torch could go out unexpectedly....

---

## Part 4: Search Design

### Why Greedy Fails

- **The failure mode:** Greedy fails here because it is trying to find the lowest cost between current and the next unvisited relic which can create more cost later (as explained part 3 as well.)
- **Counter-example setup:** S->B cost = 1, S->C cost = 1, B->D cost = 1, C->D cost 100, D-> T costs 1
- **What greedy picks:** Greedy would pick S -> C -> D -> B find no path
- **What optimal picks:** Optimal would pick S,B,D,C,T where the cost is 4
- **Why greedy loses:** Because it was unable to look ahead to see that there was a future higher cost if taking a path that takes you to the same place.

### What the Algorithm Must Explore

The algorithm must explore every order that the relics can be traveled to by the torchbearer. It must maintain the amount of fuel being used between each step so that the cost from start to finish can be minimzed. 
---

## Part 5: State and Search Space

### Part 5a: State Representation

> Document the three components of your search state as a table.
> Variable names here must match exactly what you use in torchbearer.py.

| Component | Variable name in code | Data type | Description |
|---|---|---|---|
| Current location | | | |
| Relics already collected | | | |
| Fuel cost so far | | | |

### Part 5b: Data Structure for Visited Relics

> Fill in the table.

| Property | Your answer |
|---|---|
| Data structure chosen | |
| Operation: check if relic already collected | Time complexity: |
| Operation: mark a relic as collected | Time complexity: |
| Operation: unmark a relic (backtrack) | Time complexity: |
| Why this structure fits | |

### Part 5c: Worst-Case Search Space

> Two bullets.

- **Worst-case number of orders considered:** _Your answer (in terms of k)._
- **Why:** _One-line justification._

---

## Part 6: Pruning

### Part 6a: Best-So-Far Tracking

> Three bullets.

- **What is tracked:** _Your answer here._
- **When it is used:** _Your answer here._
- **What it allows the algorithm to skip:** _Your answer here._

### Part 6b: Lower Bound Estimation

> Three bullets.

- **What information is available at the current state:** _Your answer here._
- **What the lower bound accounts for:** _Your answer here._
- **Why it never overestimates:** _Your answer here._

### Part 6c: Pruning Correctness

> One to two bullets. Explain why pruning is safe.

- _Your answer here._

---

## References

> Bullet list. If none beyond lecture notes, write that.

- _Your references here._
