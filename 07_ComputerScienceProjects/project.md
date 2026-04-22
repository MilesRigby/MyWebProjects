Computer Science Projects

<br>

This is a series of computer science-related projects built as part of _The Odin Project_. In the course, test driven development (TDD) is taught prior to these projects, however due to the "Shai-Hulud" Worm that affected npm in late 2025, I skipped ahead from the restaurant homepage project to this section while that was being fixed.

<br>

Linked List

An implementation of a singly-linked list, with comments including time complexities for each operation. The list object tracks its first element (head), last (tail), and current number of elements. Functionality includes appending new items, deleting items, popping the tail, accessing aan arbitrary index in O(n), accessing the tail in O(1), and checking if a value is present in the list. 

The slowest process is converting the list to a string, which takes O(n^2) time. I have used string concatenation to construct the string one list element at a time, and in JavaScript each concatenation takes linear time with the length of the string, resulting in O(n^2) as both the average number of steps taken to perform a concatenation and to traverse through the list increase linearly with the length of the list. This could be made linear using an array and a single .join() operation.

GitHub: https://github.com/MilesRigby/odin-linked-list

<br>

Hashmap

I implemented a hashmap using the linked list from the above project as buckets. The hashmap starts with 16 buckets, and doubles in size when the loadfactor reaches 0.75. Hashes are calculated using the unique character code of each character in a key, multiplied by a power of a prime number -31. I determine what bucket a new item goes into by the hash code modulo the number of buckets, so when resizing occurs each item either goes back into the same bucket, or a bucket in the second half of the new hashmap - e.g. an item in bucket 7 (0-indexed) of 16 can enter either bucket 7 or bucket 23 in the resized map of size 32.

This set up achieves the standard average O(1) reading, writing (amortized), and deletion for hashmaps. I have also included methods for retrieving all keys/values/entries in O(n), and an O(1) operation for retrieving the number of items (length is tracked as items are added/removed).

The resizing code is written in a way that does not directly avoid resizing within itself. This would lead to a sub-process which resizes the map again with a subset of the elements, and then continues the original resize process to add the remaining elements that weren't added previously. I beleive this is fully functional, although confusing. It also should not occur in the context of the rest of the code, since a resize splits each bucket in an initial hashmap into two buckets at most in the resized map - this means there should be no way for a resizing hashmap to use enough buckets to trigger another resize, since one of these buckets will only have one item (so can only be redistributed into one, not two, new buckets). A resize of a hashmap of size n with b used buckets and a loadfactor b/n will use at most 2b-1 buckets in the new hashmap, producing a smaller loadfactor of (2b-1)/(2n), avoiding an immediate second resize.

GitHub: https://github.com/MilesRigby/odin-hashmap

<br>

Binary Search Tree

I use a Node object constructor to build BSTs with. These are simple data structures with three accessible variables - a value, and a left and right object reference, used to store other Nodes or contain null. A BST is just a Node with a series of descendant Nodes, which can themselves be smaller BSTs (subtrees).

I build BSTs as initially balanced binary trees (the height of each node's subtrees are never different by more than 1) from arrays of values, such that items from the leftmost node to the rightmost are in sorted order. This property can then be changed with insertions and deletions, and also restored by using the rebalance method. I also created methods for determining the height (maximum distance from any descendant) and depth (distance from root) of any particular tree, as well as retrieving a node (subtree) with a specified value.

The primary feature of this implementation is the inclusion of multiple ways to iterate over the tree, providing methods for traversing the tree in level order (nodes of depth 0, then 1, etc), pre-order (value-left-right), in-order (left, value, right), and post-order (left, right, value), calling a passed in callback on each value as it goes.

The object also has a prettyPrint method for displaying the tree in a console, however this was provided by _The Odin Project_ and is not my own implementation.

GitHub: https://github.com/MilesRigby/odin-binary-search-tree

<br>

Knights Travails

This is a solver for the Knights Travails problem on an 8*8 chessboard, though the code can easily be modified to work for any finite board size, finding a smallest series of moves (other equally short paths may exist) for a chess knight piece to move from any one square to any other.

I implemented my solution using a breadth-first search of the board from the starting position, checking all possible positions within one knight's move first before continuing from each further point, ensuring to never return to a previously explored position, ensuring that a path of the shortest possible length is found by exhausting all possible paths of a given length before looking at longer ones.

The search tree is constructed using nodes, with each node storing a position - the coordinates of the board tile it relates to - and a source - the node relating to the position the knight moved to the current position from. This means for example that at a depth of 1 the tree consists of (at most, positions off the board are ignored) eight nodes, each of which stores a position one knight's move away from the starting point and holds a reference to the start node. The start node stores null as its source instead of another node.

At each node, the program checks if its position is the end target, and if it is a traceback through the nodes begins. This adds each node's position to the end of a list, then moves to the node's source. This repeats until the start node is reached (determined by it having a null source). The list of positions is then returned in reverse order so that the start position is at the start of the returned list, showing the moves in order.

GitHub: https://github.com/MilesRigby/odin-knights-travails