# Implement Stack using Queues
## https://leetcode.com/problems/implement-stack-using-queues

Implement the following operations of a stack using queues.

1. push(x) -- Push element x onto stack.
2. pop() -- Removes the element on top of the stack.
3. top() -- Get the top element.
4. empty() -- Return whether the stack is empty.
```
Example:

MyStack stack = new MyStack();

stack.push(1);
stack.push(2);  
stack.top();   // returns 2
stack.pop();   // returns 2
stack.empty(); // returns false
```
**Notes:**

1. You must use only standard operations of a queue -- which means only push to back, peek/pop from front, size, and is empty operations are valid.
2. Depending on your language, queue may not be supported natively. You may simulate a queue by using a list or deque (double-ended queue), as long as you use only standard operations of a queue.
3. You may assume that all operations are valid (for example, no pop or top operations will be called on an empty stack).


# Implementation : Using 2 Queues

```java
class MyStack {

    private Queue<Integer> q1 = new LinkedList<>();
    private Queue<Integer> q2 = new LinkedList<>();
    private int top;
    
    /** Push element x onto stack. */
    public void push(int x) {
        q1.add(x);
        top = x;
    }
    
    /** Removes the element on top of the stack and returns that element. */
    public int pop() {
        while (q1.size() > 1) {
            top = q1.remove();
            q2.add(top);
        }
        int topElement = q1.remove();
        Queue<Integer> temp = q1;
        q1 = q2;
        q2 = temp;
        return topElement;
    }
    
    /** Get the top element. */
    public int top() {
        return top;
    }
    
    /** Returns whether the stack is empty. */
    public boolean empty() {
        return q1.isEmpty();
    }
}
```

# References :
https://leetcode.com/articles/implement-stack-using-queues
