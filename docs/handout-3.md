# Transport Tycoon - Part 3

In the third exercise new requirements come up and we need to change the model and the implementation.
By using the logs and the visualization tools introduced in part 2 you have powerful tools at hand. Use these tools to understand and implement the new requirements!

## Task

- Add a new rules to the code:
  
  - **Ship can take up to 4 containers, but is slower now**:
    - Ship takes 1 hour to load *all* cargo
    - Ship takes 1 hour to unload *all* cargo
    - Ship takes 6 hours to travel in each direction
    - Note, that ship doesn't wait to be full in order to DEPART. It just LOADs the available cargo and leaves.

- Add `LOAD` and `UNLOAD` events to the domain output. They have similar schema as `ARRIVE`, are published at the beginning of the operation and have  `duration` field (`0` for TRUCK and `1` for the SHIP)

## Reference Traces

We are including reference traces so that you could compare your simulation results.

*AABABBAB* ![tt-2-AABABBAB.png](../images/tt-2-AABABBAB.png)

_ABBBABAAABBB_

![tt-2-ABBBABAAABBB.png](../images/tt-2-ABBBABAAABBB.png)
