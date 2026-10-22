#include <stdio.h>

#define MAX 100

int q1[MAX], q2[MAX];
int front1 = 0, rear1 = -1;
int front2 = 0, rear2 = -1;

void push(int x)
{
    q2[++rear2] = x;

    while (front1 <= rear1)
    {
        q2[++rear2] = q1[front1++];
    }

    int temp[MAX];
    int i, n = rear2 - front2 + 1;

    for (i = 0; i < n; i++)
        temp[i] = q2[front2 + i];

    front1 = 0;
    rear1 = n - 1;

    for (i = 0; i < n; i++)
        q1[i] = temp[i];

    front2 = 0;
    rear2 = -1;
}

int pop()
{
    if (front1 > rear1)
    {
        printf("Stack is empty\n");
        return -1;
    }

    return q1[front1++];
}

int top()
{
    if (front1 > rear1)
    {
        printf("Stack is empty\n");
        return -1;
    }

    return q1[front1];
}

int empty()
{
    return front1 > rear1;
}

int main()
{
    push(10);
    push(20);
    push(30);

    printf("Top: %d\n", top());
    printf("Pop: %d\n", pop());
    printf("Top: %d\n", top());
    printf("Empty: %d\n", empty());

    return 0;
} 
<img width="86" height="92" alt="Screenshot 2026-10-22 at 9 37 57 PM" src="https://github.com/user-attachments/assets/654ec8c8-7130-424f-9fa3-7a6537d657d6" />
