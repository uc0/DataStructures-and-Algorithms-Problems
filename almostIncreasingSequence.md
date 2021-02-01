# #1 almostIncreasingSequence

## Problem

Given a sequence of integers as an array, determine whether it is possible to obtain a strictly increasing sequence by removing no more than one element from the array.

*Note:* sequence `a0`, `a1`, ..., `an` is considered to be a strictly increasing if `a0 < a1 < ... < an`. Sequence containing only one element is also considered to be strictly increasing.



#### 	Example

- For `sequence = [1, 3, 2, 1]`, the output should be `almostIncreasingSequence(sequence) = false`.

  There is no one element in this array that can be removed in order to get a strictly increasing sequence.

- For `sequence = [1, 3, 2]`, the output should be`almostIncreasingSequence(sequence) = true`.

  You can remove `3` from the array to get the strictly increasing sequence `[1, 2]`. Alternately, you can remove `2` to get the strictly increasing sequence `[1, 3]`.



#### 	Input/Output

- **[input] array.integer sequence**

  *Guaranteed constraints:*
  `2 ≤ sequence.length ≤ 105`, `-105 ≤ sequence[i] ≤ 105`.

- **[output] boolean**

  Return `true` if it is possible to remove one element from the array in order to get a strictly increasing sequence, otherwise return `false`.



## Solutions

##### python3

```python
def almostIncreasingSequence(sequence):
    droppped = False
    last = prev = min(sequence) - 1
    
    for elm in sequence:
        if elm <= last:
            if droppped:
                return False
            else:
                droppped = True
            if elm <= prev:
                prev = last
            elif elm >= prev:
                prev = last = elm
        else:
            prev, last = last, elm
    return True
```



```python
def almostIncreasingSequence(s):
    return 3> sum((i >= j) + (i >= k) for i, j, k in zip(s, s[1:], s[2:] + [10**6]))
```



##### C++

```c++
bool almostIncreasingSequence(std::vector<int> sequence) {
    int prev = INT_MIN, preprev = INT_MIN;
    int count = 0;
    for (const auto& n : sequence) {
        if (n <= prev) {
            count++;
            if (n > preprev)
                prev = n;
        } else {
            preprev = prev;
            prev = n;
        }
    }
    return count <= 1;
}
```

