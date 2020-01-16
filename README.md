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
- [Queues and Pripority Queues](#set)
  - print()
  - enqueue()
  - dequeue()
  - front()
  - size()
  - isEmpty()
- [Binary Search tree](#set)
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
- [Binary Search Tree: Traversal & Height](#set)
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
- [Map](#set)
- [Hash Table](#set)
  - print()
  - add()
  - remove()
  - lookup()
- [Linked List](#set)
  - size()
  - head()
  - add()
  - remove()
  - isEmpty()
  - indexOf()
  - elementAt()
  - addAt()
  - removeAt()
- [Trie](#set)
- [Heap](#set)
- [Graph](#set) 
- [Graphs: breadth-first search](#set)

## Stack 
Stack is a linear data structure in which addition or removal of element follows a particular order i.e. LIFO(Last in First Out) AND FILO(First in Last Out).
- *push(item):* Adds an element to the stack
- *pop():* Removes an element from the stack, if the function is call on an empty stack it indicates “Underflow”
- *peek():* returns the top most elements in the stack, but doesn’t delete it.
- *size():* return size of stack
- *isEmpty():* return true if the stack is empty
- *printStack():* This method returns a string in which all the element of an stack is concatenated.

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
## Queues and Pripority Queues
## Binary Search tree
## Binary Search Tree: Traversal & Height
## Map
## Hash Table
## Linked List
## Trie
## Heap
## Graph 
## Graphs: breadth-first search
