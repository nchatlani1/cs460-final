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

> Document your understanding of why Dijkstra produces correct distances.
> Bullet points and short sentences throughout. No paragraphs.

### Part 3a: What the Invariant Means

> Two bullets: one for finalized nodes, one for non-finalized nodes.
> Do not copy the invariant text from the spec.

- **For nodes already finalized (in S):**
  _Your answer here._

- **For nodes not yet finalized (not in S):**
  _Your answer here._

### Part 3b: Why Each Phase Holds

> One to two bullets per phase. Maintenance must mention nonnegative edge weights.

- **Initialization : why the invariant holds before iteration 1:**
  _Your answer here._

- **Maintenance : why finalizing the min-dist node is always correct:**
  _Your answer here._

- **Termination : what the invariant guarantees when the algorithm ends:**
  _Your answer here._

### Part 3c: Why This Matters for the Route Planner

> One sentence connecting correct distances to correct routing decisions.

_Your answer here._

---

## Part 4: Search Design

### Why Greedy Fails

> State the failure mode. Then give a concrete counter-example using specific node names
> or costs (you may use the illustration example from the spec). Three to five bullets.

- **The failure mode:** _Your answer here._
- **Counter-example setup:** _Your answer here._
- **What greedy picks:** _Your answer here._
- **What optimal picks:** _Your answer here._
- **Why greedy loses:** _Your answer here._

### What the Algorithm Must Explore

> One bullet. Must use the word "order."

- _Your answer here._

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
