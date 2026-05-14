# Development Log – The Torchbearer

**Student Name:** Nitin Chatlani
**Student ID:** 827870037

> Instructions: Write at least four dated entries. Required entry types are marked below.
> Two to five sentences per entry is sufficient. Write entries as you go, not all in one
> sitting. Graders check that entries reflect genuine work across multiple sessions.
> Delete all blockquotes before submitting.

---

## Entry 1 – [5.13.26 1pm]: Initial Plan

> Required. Write this before writing any code. Describe your plan: what you will
> implement first, what parts you expect to be difficult, and how you plan to test.

I am planning to work through this assignment in four segments. First, I will work on the skeleton in Readme. I will focus code attention on Dijkstra's + precomputation first since those are needed to complete the rest of the parts. I will then work on the backtracking search so I can figure out the slower search methodology to verify. Last will be pruning since we will have verified answers and are now able to optimize how we get them. Lastly,  the solve pipeline. Then comparing values to confirm that its valid against the initial results.  
---

## Entry 2 – [5.13.26 3:14pm]: [Dijsktras + Precompute Distances]

Created the nested dictionary structure to allow for lookups to be in O(1) time. Implemented Dijkstras and the Precompute_Distances functions. Considered which paths needed to be calculated for Dijsktras algorithm to perform without any extra overhead. 

---

## Entry 3 – [5.13.26 7:34pm]: [_explore() + relics_remaining implemented]

Implemented _explore(). relics_remaining hits the base case when it becomes empty. The recursive case is running through the still remaining relics, creating new paths, and backtracks as needed. During the development of these two functions I was running into an issue where, when traced, the cost would be correct but the order that should be traveled for optimizing the fuel was incorrect. My code had both a pop() before recursion and then a .add(relic) after which led to new branches colliding into old ones. This was remedied by adding the pop() after the recursive call instead of before it. This ensured that each branch would be empty when it started being formed.
---

## Entry 4 – [Date]: Post-Implementation Reflection

> Required. Written after your implementation is complete. Describe what you would
> change or improve given more time.

_Your entry here._

---

## Final Entry – [Date]: Time Estimate

> Required. Estimate minutes spent per part. Honesty is expected; accuracy is not graded.

| Part | Estimated Hours |
|---|---|
| Part 1: Problem Analysis | |
| Part 2: Precomputation Design | |
| Part 3: Algorithm Correctness | |
| Part 4: Search Design | |
| Part 5: State and Search Space | |
| Part 6: Pruning | |
| Part 7: Implementation | |
| README and DEVLOG writing | |
| **Total** | |
