# Data Structure Javascript

Data Structure and methods
- [Stack](#stack)
  - push(item) 
  - pop() 
  - peek() 
  - size()
  - isEmpty() 
  - printStack() 
- [Set](#set)
  - add()
  - remove()
  - has()
  - values()
  - size()
  - union()
  - intersection()
  - difference()
  - subset()
- [Queues and Pripority Queues](#queues-and-pripority-queues)
  - print()
  - enqueue()
  - dequeue()
  - front()
  - size()
  - isEmpty()
- [Binary Search tree](#binary-search-tree)
  - add()
  - findMin()
  - findMax()
  - find(data)
  - isPresent(data)
  - remove(data)
  - isBalanced()
  - findMinHeight(node)
  - findMaxHeight(node)
  - inOrder()
  - preOrder()
  - postOrder()
  - levelOrder()
- [Binary Search Tree: Traversal & Height](#binary-search-tree-traversal--height)
  - add()
  - findMin()
  - findMax()
  - find(data)
  - isPresent(data)
  - remove(data)
  - isBalanced()
  - findMinHeight(node)
  - findMaxHeight(node)
  - inOrder()
  - preOrder()
  - postOrder()
  - levelOrder()
- [Map](#map)
- [Hash Table](#hash-table)
  - print()
  - add()
  - remove()
  - lookup()
- [Linked List](#linked-list)
  - size()
  - head()
  - add()
  - remove()
  - isEmpty()
  - indexOf()
  - elementAt()
  - addAt()
  - removeAt()
- [Trie](#trie)
  - add()
  - isWord()
  - print()
- [Heap](#heap)
  - MinHeap()
    - print()
    - insert()
    - remove()
    - sort()
  - MaxHeap()
    - print()
    - insert()
    - remove()
- [Graph](#graph) 
- [Graphs: breadth-first search](#graphs-breadth-first-search)
Time complexcity
## Stack 
Stack is a linear data structure in which addition or removal of element follows a particular order i.e. LIFO(Last in First Out) AND FILO(First in Last Out).

A real-world example is a stack of plates. we can see that the plate that is inserted last is the first one to be taken off.

Time complexity
If you don’t know much about time complexity, you’ll be lost until you read this short article on time complexity in JavaScript. For each method on the stack, the worst-case time complexity is constant — O(1). This means that as the stack grows to n size, each method completes its job in the same amount of time.
push: Constant — O(1)
pop: Constant — O(1)
peek: Constant — O(1)
empty: Constant — O(1)
size: Constant — O(1)
swap: Constant — O(1)

- **push(item):** Adds an element to the stack
- **pop():** Removes an element from the stack, if the function is call on an empty stack it indicates “Underflow”
- **peek():** returns the top most elements in the stack, but doesn’t delete it.
- **size():** return size of stack
- **isEmpty():** return true if the stack is empty
- **printStack():** This method returns a string in which all the element of an stack is concatenated.

  ![Stack vs Queue](images/stack_vs_queue.png)

### Method one
```javascript
// Creates a stack
var Stack = function() {
    this.count = 0;
    this.storage = {};
  
    // Adds a value onto the end of the stack
    this.push = function(value) {
        this.storage[this.count] = value;
        this.count++;
    }
    
    // Removes and returns the value at the end of the stack
    this.pop = function() {
        if (this.count === 0) {
            return undefined;
        }

        this.count--;
        var result = this.storage[this.count];
        delete this.storage[this.count];
        return result;
    }
    
    this.size = function() {
        return this.count;
    }
    
    // Returns the value at the end of the stack
    this.peek = function() {
        return this.storage[this.count-1];
    }
}

var myStack = new Stack();

myStack.push(1);
myStack.push(2);
console.log(myStack.peek()); // 2
console.log(myStack.pop()); // 2
console.log(myStack.peek()); // 1
myStack.push("Suryansh");
console.log(myStack.size()); // 2
console.log(myStack.peek()); // Suryansh
console.log(myStack.pop()); // Suryansh
console.log(myStack.peek()); // 1
```

### Method Two
```javascript
class Stack {

    // Array is used to implement stack
    constructor() {
        this.items = [];
    }

    // push function
    push(element) {
        // push element into the items
        this.items.push(element);
    }

    // pop function
    pop() {
        // return top most element in the stack
        // and removes it from the stack
        // Underflow if stack is empty
        if (this.items.length == 0)
            return "Underflow";
        return this.items.pop();
    }

    // peek function
    peek() {
        // return the top most element from the stack
        // but does'nt delete it.
        return this.items[this.items.length - 1];
    }
    
    size() {
        return this.items.length;
    }
    // Helper methods
    // isEmpty function
    isEmpty() {
        // return true if stack is empty
        return this.items.length == 0;
    }
    
    // printStack function
    printStack() {
        var str = "";
        for (var i = 0; i < this.items.length; i++)
            str += this.items[i] + " ";
        return str;
    }
}

var myStack = new Stack();

myStack.push(1);
myStack.push(2);
console.log(myStack.peek()); // 2
console.log(myStack.pop()); // 2
console.log(myStack.peek()); // 1
myStack.push("Suryansh");
console.log(myStack.size()); // 2
console.log(myStack.peek()); // Suryansh
console.log(myStack.pop()); // Suryansh
console.log(myStack.peek()); // 1
myStack.printStack() // "1 "
```

## Set

```javascript
/* Sets */

function mySet() {
    // the var collection will hold the set
    var collection = [];
    // this method will check for the presence of an element and return true or false
    this.has = function(element) {
        return (collection.indexOf(element) !== -1);
    };
    // this method will return all the values in the set
    this.values = function() {
        return collection;
    };
    // this method will add an element to the set
    this.add = function(element) {
        if(!this.has(element)){
            collection.push(element);
            return true;
        }
        return false;
    };
    // this method will remove an element from a set
    this.remove = function(element) {
        if(this.has(element)){
            index = collection.indexOf(element);
            collection.splice(index,1);
            return true;
        }
        return false;
    };
    // this method will return the size of the collection
    this.size = function() {
        return collection.length;
    };
    // this method will return the union of two sets
    this.union = function(otherSet) {
        var unionSet = new mySet();
        var firstSet = this.values();
        var secondSet = otherSet.values();
        firstSet.forEach(function(e){
            unionSet.add(e);
        });
        secondSet.forEach(function(e){
            unionSet.add(e);
        });
        return unionSet;
    };
    // this method will return the intersection of two sets as a new set
    this.intersection = function(otherSet) {
        var intersectionSet = new mySet();
        var firstSet = this.values();
        firstSet.forEach(function(e){
            if(otherSet.has(e)){
                intersectionSet.add(e);
            }
        });
        return intersectionSet;
    };
    // this method will return the difference of two sets as a new set
    this.difference = function(otherSet) {
        var differenceSet = new mySet();
        var firstSet = this.values();
        firstSet.forEach(function(e){
            if(!otherSet.has(e)){
                differenceSet.add(e);
            }
        });
        return differenceSet;
    };
    // this method will test if the set is a subset of a different set
    this.subset = function(otherSet) {
        var firstSet = this.values();
        return firstSet.every(function(value) {
          return otherSet.has(value);
        });
    };
}
var setA = new mySet();  
var setB = new mySet();  
setA.add("a");  
setB.add("b");  
setB.add("c");  
setB.add("a");  
setB.add("d");  
console.log(setA.subset(setB));
console.log(setA.intersection(setB).values());
console.log(setB.difference(setA).values());

var setC = new Set();  
var setD = new Set();  
setC.add("a");  
setD.add("b");  
setD.add("c");  
setD.add("a");  
setD.add("d");  
console.log(setD.values())
setD.delete("a");
console.log(setD.has("a"));
console.log(setD.add("d"));
```

## Queues and Pripority Queues
A Queue works on the FIFO(First in First Out) principle. Hence, it performs two basic operations that is addition of elements at the end of the queue and removal of elements from the front of the queue. Like Stack, Queue is also a linear data structure.

A queue is like a line at a restaurant. It’s “first in, first out” (FIFO), which means that the item that was put in the queue longest ago is the first item that comes out. “First come, first served.”


Queues have two main methods:

enqueue() : Adds a node (value)
dequeue() : Removes and returns the next node in the queue

They can also include other utility methods:
peek() : Returns the node at the front of the queue (without removing)
isEmpty() : Returns True if the queue is empty, otherwise returns false

enqueue: Constant — O(1)
dequeue: Constant — O(1)

Code
peek: Constant — O(1)
isEmpty: Constant — O(1)
```javascript
/* Queues */

function Queue () { 
    collection = [];
    this.print = function() {
        console.log(collection);
    };
    this.enqueue = function(element) {
        collection.push(element);
    };
    this.dequeue = function() {
        return collection.shift(); 
    };
    this.front = function() {
        return collection[0];
    };
    this.size = function() {
        return collection.length; 
    };
    this.isEmpty = function() {
        return (collection.length === 0); 
    };
}

var q = new Queue(); 
q.enqueue('a'); 
q.enqueue('b');
q.enqueue('c');
q.print();
q.dequeue();
console.log(q.front());
q.print();


function PriorityQueue () {
    var collection = [];
    this.printCollection = function() {
      (console.log(collection));
    };
    this.enqueue = function(element){
        if (this.isEmpty()){ 
            collection.push(element);
        } else {
            var added = false;
            for (var i=0; i<collection.length; i++){
                 if (element[1] < collection[i][1]){ //checking priorities
                    collection.splice(i,0,element);
                    added = true;
                    break;
                }
            }
            if (!added){
                collection.push(element);
            }
        }
    };
    this.dequeue = function() {
        var value = collection.shift();
        return value[0];
    };
    this.front = function() {
        return collection[0];
    };
    this.size = function() {
        return collection.length; 
    };
    this.isEmpty = function() {
        return (collection.length === 0); 
    };
}

var pq = new PriorityQueue(); 
pq.enqueue(['Beau Carnes', 2]); 
pq.enqueue(['Quincy Larson', 3]);
pq.enqueue(['Ewa Mitulska-Wójcik', 1])
pq.enqueue(['Briana Swift', 2])
pq.printCollection();
pq.dequeue();
console.log(pq.front());
pq.printCollection();

```

## Binary Search tree
## Binary Search Tree: Traversal & Height
## Map
## Hash Table
## Linked List
## Trie
## Heap
## Graph 
## Graphs: breadth-first search
