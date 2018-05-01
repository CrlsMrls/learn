# Stacks & Queues

## Resizing arrays vs Linked list

*Linked-list*
* every operation (stacks & queues) takes constant time in the worst case
* uses extra time and space to deal with the links
* reading one specific value in ordered linked-list: O(n) 


*Resizing-array*
* Every operation takes constant *amortized* time
* less wasted space
* reading one specific value: O(1)
* inserting in an ordered array could have linear time O(n)

# Linked lists

List problems often have a simple **brute-force solution that uses 0(n) space**, but a subtler solution that uses the existing list nodes to reduce space complexity to 0(1).

Very often, a problem on lists is conceptually simple, and is more about cleanly coding what's specified, rather than designing an algorithm. 

Consider using a dummy head (sometimes referred to as a sentinel) to avoid having to check for empty lists. This simplifies code, and makes bugs less likely.

It's easy to forget to update next (and previous for double linked list) for the head and tail. 

Runner technique: Algorithms operating on singly linked lists often benefit from using two iterators, one ahead of the other, or one advancing quicker than the other. The fast node might be ahead by a fixed amount.

Remember to ask if it is a singly or a doubly linked list.


 

