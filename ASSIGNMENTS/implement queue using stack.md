#include <stdio.h>

#define MAX 100

int input[MAX], output[MAX];
int top1 = -1, top2 = -1;

void push(int x)
{
    input[++top1] = x;
}

void transfer()
{
    if (top2 == -1)
    {
        while (top1 != -1)
        {
            output[++top2] = input[top1--];
        }
    }
}

int pop()
{
    transfer();
    return output[top2--];
}

int peek()
{
    transfer();
    return output[top2];
}

int empty()
{
    return top1 == -1 && top2 == -1;
}

int main()
{
    push(10);
    push(20);
    push(30);

    printf("Peek: %d\n", peek());
    printf("Pop: %d\n", pop());
    printf("Peek: %d\n", peek());
    printf("Empty: %d\n", empty());

    return 0;
} 

<img width="93" height="80" alt="Screenshot 2026-10-22 at 9 34 50 PM" src="https://github.com/user-attachments/assets/4b190ba6-a47d-4943-b878-ab7305d96f95" />
