# Transport Tycoon - Part 1

There is a map containing a Factory, Port, Warehouse A and Warehouse B. Factory has a small stock of containers that have to be delivered to these warehouses in a predefined order.

![tt-1-exercise.png](../images/tt-1-exercise.png)

There are **two trucks and one ship that can carry one container at a time** (trucks start at Factory, ship starts at the Port).

**Traveling takes a specific amount of hours** (represented by an orange number). Time is needed to travel in one direction, you also spend the same amount of time to come back.
For example, it takes 5 hours for a truck to travel from the Factory to B.

Transport follows a simple heuristic: **pick the first container from the location** (first-in, first - out), bring it to the designation, then come back home.

Truck that drops off cargo at the Port doesn't need to wait for the ship (there is a small warehouse buffer there). It can drop the cargo and start heading back. Cargo loading and unloading is an instant operation.

Transport moves *in parallel*. First truck might be bringing container to a location A, while the second truck comes back from A, while ship travels back to the Port.

## Task

**Task**: write a program that takes a list of cargos from the command line and prints out the number of hours that it would take to get them delivered.

### Samples

| Input        | Output |
| ------------ | ------ |
| A            | 5      |
| AB           | 5      |
| BB           | 5      |
| ABB          | 7      |
| AABABBAB     | ?      |
| ABBBABAAABBB | ?      |

Why does it take 7 hours to finish `ABB`?

| Time  | Truck 1  | Truck 2 | Ship |
| ------|----------|---------|------|
|  0    | loads & leaves for Port | loads & leaves for B | |
| 1     | Arrives at Port, unloads & heads back to Factory |  | loads & leaves for A |
| 2     | Arrives back at the Factory, loads & leaves for B | | |
| 5     | | Arrives at B, unloads & heads back to Factory | Arrives at A, unloads & heads back to Port |
| 7     | Arrives at B, unloads & heads back to Factory | | |
| 9     | | | Arrives back at the Port|
| 10    | | Arrives back at the Factory |
| 12    | Arrives back at the Factory | |

## Exercise Notes

- Don't worry about making the code extensible. We will evolve the codebase, but the deeper domain dive will have to start from the scratch.

- Don't worry if your numbers don't exactly match answers from your colleagues. There is a small loop-hole in the exercise that makes it non-deterministic. We will address it later.

- While picking the language for the exercise, pick whatever that would let you solve the problem quicker. If you are itching to try out a new fancy language that you are less familiar with, there will be a chance for that later.

- Remember that all processes happen in parallel. Trucks and ship would be moving around the map at the same time, not sequentially.

- The order of the containers is only relevant at their pickup at the factory. Once they are on their way, we only care that at some point they arrive at their destination.

- If you don’t make any progress in the beginning, try to reduce the problem to a simpler case and work from there.

- Don't worry about applying any patterns (e.g. aggregates or events) at this point. Just get the job done. Implementation patterns will emerge in the codebase later.

## Bonus points

1. What is the possible reason for the different solutions to return different answers?
2. Link your solution in the *solution list* at [https://github.com/Softwarepark/exercises/blob/master/transport-tycoon/README.md](https://github.com/Softwarepark/exercises/blob/master/transport-tycoon/README.md).
