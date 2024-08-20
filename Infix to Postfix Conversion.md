# Infix to Postfix Conversion

### 1.	WAP in C to implement the algorithm to convert an infix expression into its equivalent postfix using Stack. 

> Test Data

    Enter the Infix expression : A+b-c/d
    
> Expected Output

     Postfix Expression is : A b + c d / -

> Source Code

```c


#include<stdio.h>
#include<ctype.h>
char stack[100];
int top = -1; 


void push(char x)
{
    stack[++top] = x;
}



char pop()
{
    if(top == -1)
        return -1;
    else
        return stack[top--];
}



int priority(char x)
{
    if(x == '(' )
        return 0;
    if(x == '+' || x == '-')
        return 1;
    if(x == '*' || x == '/')
        return 2;

    return 0;
}



int main()
{
    char exp[100];
    char *e, x;
    printf("\n Enter the Infix expression : ");
    scanf("%s",exp);
    e = exp;
    printf("\n Postfix Expression is : ");
    while(*e != '\0')
    {
        if(isalnum(*e))
            printf("%c ",*e);
        else if(*e == '(' )
            push(*e);
        else if(*e == ')' )
        {
            while((x = pop()) != '(' )
                printf("%c ", x);
        }
        else
        {

            while(priority(stack[top]) >= priority(*e))
                printf("%c ",pop());
            push(*e);
        }
        e++;
    }

    while(top != -1)
    {
        printf("%c ",pop());
    }

return 0;
}
```
<br>

#  Postfix Conversion

### 2.	WAP in C to implement the algorithm to evaluate a postfix expression using Stack.  

> Source Code

```c

#include <stdio.h>  
#include <stdlib.h>  
#define MAX_SIZE 20 


// Stack implementation  
int stack[MAX_SIZE];  
int top = -1;  
void push(int item) {  
    if (top >= MAX_SIZE - 1) {  
printf("Stack Overflow\n");  
        return;  
    }  
    top++;  
    stack[top] = item;  
}  



int pop() {  
    if (top < 0) {  
printf("Stack Underflow\n");  
        return -1;  
    }  
    int item = stack[top];  
    top--;  
    return item;  
} 



int is_operator(char symbol) {  
    if (symbol == '+' || symbol == '-' || symbol == '*' || symbol == '/') {  
        return 1;  
    }  
    return 0;  
}  




int evaluate(char* expression) {  
    int i = 0;  
    char symbol = expression[i];  
    int operand1, operand2, result;  
  
    while (symbol != '\0') {  
        if (symbol >= '0' && symbol <= '9') {  
            int num = symbol - '0';  
            push(num);  
        }  
        else if (is_operator(symbol)) {  
            operand2 = pop();  
            operand1 = pop();  
            switch(symbol) {  
                case '+': result = operand1 + operand2; break;  
                case '-': result = operand1 - operand2; break;  
                case '*': result = operand1 * operand2; break;  
                case '/': result = operand1 / operand2; break;  
            }  
            push(result);  
        }  
i++;  
        symbol = expression[i];  
    }  
    result = pop();  
    return result;  
}  




int main() {  
    char expression[] = "231*+9-";  
    int result = evaluate(expression);  
printf("Result = %d\n", result);  
return 0;  
}
```





