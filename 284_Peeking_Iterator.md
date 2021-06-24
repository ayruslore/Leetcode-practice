## Question : Peeking Iterator

Design an iterator that supports the peek operation on a list in addition to the hasNext and the next operations. Implement the PeekingIterator class:
1. PeekingIterator(int[] nums) Initializes the object with the given integer array nums.
2. int next() Returns the next element in the array and moves the pointer to the next element.
3. bool hasNext() Returns true if there are still elements in the array.
4. int peek() Returns the next element in the array without moving the pointer.

## Solution :

```python3
# Below is the interface for Iterator, which is already defined for you.
#
# class Iterator:
#     def __init__(self, nums):
#         """
#         Initializes an iterator object to the beginning of a list.
#         :type nums: List[int]
#         """
#
#     def hasNext(self):
#         """
#         Returns true if the iteration has more elements.
#         :rtype: bool
#         """
#
#     def next(self):
#         """
#         Returns the next element in the iteration.
#         :rtype: int
#         """

class PeekingIterator:
    def __init__(self, iterator):
        """
        Initialize your data structure here.
        :type iterator: Iterator
        """
        self.iterator = iterator
        self.current = self.iterator.next()
        self.after = -1
        if self.iterator.hasNext():
            self.after = self.iterator.next()

    def peek(self):
        """
        Returns the next element in the iteration without advancing the iterator.
        :rtype: int
        """
        return self.current

    def next(self):
        """
        :rtype: int
        """
        res = self.current
        self.current = self.after
        if self.iterator.hasNext():
            self.after = self.iterator.next()
        else:
            self.after = -1
        return res

    def hasNext(self):
        """
        :rtype: bool
        """
        if self.current == -1:
            return False
        return True

# Your PeekingIterator object will be instantiated and called as such:
# iter = PeekingIterator(Iterator(nums))
# while iter.hasNext():
#     val = iter.peek()   # Get the next element but not advance the iterator.
#     iter.next()         # Should return the same value as [val].
```
