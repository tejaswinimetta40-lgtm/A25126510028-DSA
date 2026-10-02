#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *left;
    struct Node *right;
};

struct Node* createNode(int value) {
    struct Node *newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

struct Node* insert(struct Node *root, int value) {
    if (root == NULL) return createNode(value);
    if (value < root->data) root->left = insert(root->left, value);
    else if (value > root->data) root->right = insert(root->right, value);
    return root;
}

void inorder(struct Node *root) {
    if (root == NULL) return;
    inorder(root->left);
    printf("%d ", root->data);
    inorder(root->right);
}

struct Node* findMin(struct Node *root) {
    while (root->left != NULL) {
        root = root->left;
    }
    return root;
}

struct Node* deleteNode(struct Node *root, int value) {
    if (root == NULL) {
        printf("Value %d not found in the BST\n", value);
        return root;
    }

    if (value < root->data) {
        root->left = deleteNode(root->left, value);
    } else if (value > root->data) {
        root->right = deleteNode(root->right, value);
    } else {
        // node found

        // Case 1: no children (leaf node)
        if (root->left == NULL && root->right == NULL) {
            free(root);
            return NULL;
        }
        // Case 2: one child
        else if (root->left == NULL) {
            struct Node *temp = root->right;
            free(root);
            return temp;
        }
        else if (root->right == NULL) {
            struct Node *temp = root->left;
            free(root);
            return temp;
        }
        // Case 3: two children
        else {
            struct Node *successor = findMin(root->right);
            root->data = successor->data;
            root->right = deleteNode(root->right, successor->data);
        }
    }
    return root;
}

int main() {
    struct Node *root = NULL;
    int n, value;

    printf("Enter number of values to insert: ");
    scanf("%d", &n);

    printf("Enter %d values:\n", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &value);
        root = insert(root, value);
    }

    printf("\nInorder before deletion: ");
    inorder(root);
    printf("\n");

    // Case 1: delete a leaf node
    printf("\n--- Deleting leaf node 20 ---\n");
    root = deleteNode(root, 20);
    printf("Inorder after deletion: ");
    inorder(root);
    printf("\n");

    // Case 2: delete a node with one child
    printf("\n--- Deleting node with one child (60) ---\n");
    root = deleteNode(root, 60);
    printf("Inorder after deletion: ");
    inorder(root);
    printf("\n");

    // Case 3: delete a node with two children
    printf("\n--- Deleting node with two children (30) ---\n");
    root = deleteNode(root, 30);
    printf("Inorder after deletion: ");
    inorder(root);
    printf("\n");

    return 0;
}

<img width="510" height="355" alt="WhatsApp Image 2026-10-02 at 17 14 03" src="https://github.com/user-attachments/assets/2b817c6b-b2dc-4464-8fad-99d8c5a3c159" />
