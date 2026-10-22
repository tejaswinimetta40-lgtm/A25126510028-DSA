#include <stdio.h>
#include <string.h>

#define MAX 10000

int isValid(char s[])
{
    char stack[MAX];
    int top = -1;

    for (int i = 0; s[i] != '\0'; i++)
    {
        char c = s[i];

        if (c == '(' || c == '{' || c == '[')
        {
            stack[++top] = c;
        }
        else
        {
            if (top == -1)
                return 0;

            char ch = stack[top--];

            if ((c == ')' && ch != '(') ||
                (c == '}' && ch != '{') ||
                (c == ']' && ch != '['))
            {
                return 0;
            }
        }
    }

    return top == -1;
}

int main()
{
    char s[] = "({[]})";

    if (isValid(s))
        printf("true\n");
    else
        printf("false\n");

    return 0;
} 
output:
<img width="139" height="57" alt="Screenshot 2026-10-22 at 9 51 04 PM" src="https://github.com/user-attachments/assets/064242d9-2863-432b-a597-2f201a41d813" />
