#### Please add your answers to the ***Analysis of  Algorithms*** exercises here.

## Exercise I

a) Runtime: O(n)
The runtime complexity of this block of code would be `O(n^3)` (polynomial), where `n` is the input size. This is because the `while` loop is running on the order on `n^3` times. While the code in the loop is incrementing by a value on the order of `n^2`, the higher polynomial order of `n^3` will dominate the `n^2` for large inputs.


b) Runtime: O(n log n)
The runtime complexity of this block of code would be `O(n log n)` (linearithmic), where `n` is the input size. This is because the outer `for` loop runs `n` times, for a runtime complexity of `O(n)`. Meanwhile, the value of `j` in the inner `while` loop is doubling rather than incremening, resulting in a runtime complexity of `O(log )`. For nested loops, we want to multiply the runtime complexities, so we would get a combined runtime complexity of `O(n log n)`.

c) Runtime: O(n)
The runtime complexity of this block of code would be `O(n)` (linear), where `n` is `bunnies`. This block of code demonstrates recursion and will run `n` times, decrementing `bunnies` down to the base case value of zero.


## Exercise II
## Proposed algorithm:

1. Start at the _moddle_ floor.
2. Drop an egg from this floor. If the egg breaks, eliminate _all the floors above_.
3. If the egg doesn't break, eliminate _current floor and all the floors below_.
4. Repeat the process with the uneliminated floors until there are only two floors left; 'f' would be the higher of the two floors.

## Pseudocode (iterative solution):
 Both solutions assume a function 'dropped_egg_breaks()' that returns true if the egg dropped from a particular floor breaks or false if the dropped egg doesn't break.

 ```
 def iterative_minimize_broken_eggs (floors):
    #initialize low floor and high floors
    low_floor = 0
    high_floor = len(floors) - 1

    #run code while there are more than two floors remaining
    while low_floor <= high_fllor - 1:

        #find middle floor
        middle_floor = (low_floor + high_floor) // 2

        #if dropped egg breaks, reset high floor to eliminate above floors
        if dropped_egg_breaks(middle_floor):
            high_floor = middle_floor

        #if dropped egg doesn't break, reset low floor to eliminate current floor and all floors below
        elif not dropped_egg_breaks(middle_floor):
            low_floor = middle_floor + 1

    # while loops ends when we're left with teo floors, return the higher floor as f
    return high_floor

    # keep in mind that floors list is 0 indexed, so f would correspond to the "f + 1"th floor

    ```

    ### Pseudocode (recursive solution):

    ```
    def recursive_minimize_broken_eggs(floors):
        # find the middle floor
        middle_floor = len(floors) // 2

        # run code while there are more than two floors remaining
        while len(floors) > 2:

            # if dropped egg breaks, reset high floor to eliminate above floors
            if dropped_egg_breaks(middle_floor):
                return recursive_minimize_broken_eggs(floors[:middle_floor])
        
            # if dropped egg doesn't break, reset low floor to eliminate current floor and all floors below
            elif not dropped_egg_breaks(middle_floor):
                return recursive_minimize_broken_eggs(floors[middle_floor + 1:])

        # return the higher of the two floors as f
        return floor[1]

    ```

    ### Runtime Complexity:

    This solution implements a variation on a `Binary Search` and thus has a logarithmic runtime complexity of `O(log n)`. As the number of floors increases, the runtime used will grow at a **slightly slower** rate, so this solution would perform better than linear `O(n)`.


