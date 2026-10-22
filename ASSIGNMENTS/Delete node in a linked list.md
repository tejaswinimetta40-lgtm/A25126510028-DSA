#include <stdio.h>
#include <stdlib.h>

struct ListNode {
    int val;
    struct ListNode *next;
};

void deleteNode(struct ListNode *node)
{
    struct ListNode *temp;

    node->val = node->next->val;

    temp = node->next;
    node->next = node->next->next;

    free(temp);
}

int main()
{
    struct ListNode *head, *n1, *n2, *n3;

    n1 = malloc(sizeof(struct ListNode));
    n2 = malloc(sizeof(struct ListNode));
    n3 = malloc(sizeof(struct ListNode));

    n1->val = 10;
    n1->next = n2;

    n2->val = 20;
    n2->next = n3;

    n3->val = 30;
    n3->next = NULL;

    head = n1;

    deleteNode(n2);

    while (head != NULL)
    {
        printf("%d ", head->val);
        head = head->next;
    }

    return 0;
} 
<img width="148" height="52" alt="Screenshot 2026-10-22 at 9 53 45 PM" src="https://github.com/user-attachments/assets/91bb2797-36f2-40f2-b1f9-19932c3db575" />
