# Stack
### 1. 	WAP in C to implement the basic operations of Stack. 

> Source Code

```c
#include <stdio.h>
#define MAX_SIZE 100

int stack[MAX_SIZE];
int top = -1;


void push(int data) 
{
    if (top == MAX_SIZE - 1) {
        printf("Stack is full\n");
        return;
    }
    stack[++top] = data;
}


int pop() 
{
    if (top == -1) {
        printf("Stack is empty\n");
        return -1;
    }
    return stack[top--];
}



int isEmpty() 
{
    return top == -1;
}


int getTop()
 {
    if (top == -1) {
        printf("Stack is empty\n");
        return -1;
    }
    return stack[top];
}


void  Display_Stack() 
{
    for (int i = top; i >= 0; i--) {
        printf("%d ", stack[i]);
    }
    printf("\n");
}


int main()
 {
    push(1); // insertion
    push(2); // insertion
    push(3); // insertion
    Display_Stack(); // Display
    printf("Top element: %d\n", getTop());  // Top most elements print
    printf("Popped element: %d\n", pop());  // Deletion
    Display_Stack();  // Display
    return 0;
}
```

<br>

### 2.  WAP in C to implement reversal of a string using Stack. 

> Source Code

```c

#include<stdio.h>
int main()
{
	int top=0,i=0,j=0;
	
	char string[100],stack[100],rev[100];
	
	printf("\n Enter the any string: ");
	gets(string);
	
	while(string[i] != '\0')
	{
		top++;
		stack[top] = string[i];
		i++;
	}

	while(top != 0)
	{
		rev[j] = stack[top];
		top--;
		j++;
	}
    rev[j] = '\0';
    
	printf("\n Reversal of string is : %s",rev);
	return 0;
}  
```

# Queue
### 3.  WAP in C to implement the basic operations of Queue. 

> Source Code

```c
#include <stdio.h>
#define MAX_SIZE  5
int queue[MAX_SIZE];
int front = -1;
int rear = -1;



void enqueue(int data) 
{
    if (rear == MAX_SIZE-1) {
        printf("Queue is full\n");
        return;
    }

    else
    {
        if(front == -1)
        {
            rear = front = 0;
        }
    else
    {
     rear = rear+1;
    }
    queue[rear] = data;
 }
}



int dequeue() 
{
    if (front == -1 || front == rear+1) {
        printf("Queue is empty\n");
        return -1;
    }
    int data = queue[front];
    front++;
    return data;
}



int isEmpty() {
    return front == -1;
}



int getFront() {
    if (front == rear) {
        printf("Queue is empty\n");
        return -1;
    }
    return queue[front];
}



void Display() {
    if (front == -1 || front==rear+1) {
        printf("Queue is empty\n");
        return;
    }
    for (int i = front; i <= rear; i++) {
        printf("%d ", queue[i]);
    }
    printf("\n");
}



int main() {
    enqueue(1); // insertion 
    enqueue(2); // insertion
    enqueue(3); // insertion
    Display();  // Display 
    printf("Front element: %d\n", getFront()); // Front Elements
    printf("Dequeued element: %d\n", dequeue());  // Deletion
    Display(); // Display
    return 0;
}
```

<br>

# Circular Queue
### 4.  WAP in C to implement the basic operations of Queue. 

> Source Code

```c
#include<stdio.h>
#define capacity 6
int queue[capacity];
int front = -1, rear = -1;



int checkFull ()
{
  if ((front == rear + 1) || (front == 0 && rear == capacity - 1))
    {
      return 1;
    }
  return 0;
}



int checkEmpty ()
{
  if (front == -1)
    {
      return 1;
    }
  return 0;
}



void enqueue (int val)
{
  if (checkFull ())
    printf ("\n\t [Queue  is Overflow] \n");

  else
    {
      if (front == -1)
	front = 0;

      rear = (rear + 1) % capacity;
      queue[rear] = val;
      printf ("%d was enqueued to circular queue\n", val);
    }
}



int dequeue ()
{
  int var;
  if (checkEmpty ())
    {
      printf ("\n\t [Queue is Underflow] \n");
      return -1;
    }
  else
    {
      var = queue[front];
      if (front == rear)
	{
	  front = rear = -1;
	}
      else
	{
	  front = (front + 1) % capacity;
	}
      printf("%d was dequeued from circular queue\n", var);
      return 1;
    }
}



void print ()
{
  int i;
  if (checkEmpty ())
    printf ("\n[Nothing to dequeue]\n");
  else
    {
      printf ("\nThe queue looks like: \n");
      for (i = front; i != rear; i = (i + 1) % capacity)
	{
	  printf ("%d ", queue[i]);
	}
      printf ("%d \n\n", queue[i]);
}
}

int main ()
{
  dequeue ();

  enqueue (15); // insertion
  enqueue (20); // insertion
  enqueue (25); // insertion
  enqueue (30); // insertion
  enqueue (35); // insertion

  print (); // Display
  dequeue (); // Deletion
  dequeue (); // Deletion

  print (); // Display

  enqueue (40);  // insertion
  enqueue (45);  // insertion
  enqueue (50);  // insertion
  enqueue (55);  // insertion will not possible because overflow condition is true	
  print (); // Display
}
```
<br>
