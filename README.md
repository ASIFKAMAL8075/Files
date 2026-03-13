https://www.onlinegdb.com/0m5S-FOsJj


https://drive.google.com/drive/folders/19W3X8s5tWeRiM5mxVW6qGNP_SiTiaw5i?usp=sharing



1. C program to create a Binary Search Tree (BST), insert elements, and perform inorder traversal

#include <stdio.h>
#include <stdlib.h>

// Structure of a node in BST
struct node {
    int data;
    struct node *left;
    struct node *right;
};

// Function to create a new node
struct node* createNode(int value) {
    struct node* newNode = (struct node*)malloc(sizeof(struct node));
    newNode->data = value;      // store value in node
    newNode->left = NULL;       // initially left child is NULL
    newNode->right = NULL;      // initially right child is NULL
    return newNode;
}

// Function to insert a node into BST
struct node* insert(struct node* root, int value) {

    // If tree is empty, create the root node
    if (root == NULL)
        return createNode(value);

    // If value is smaller, insert into left subtree
    if (value < root->data)
        root->left = insert(root->left, value);

    // If value is greater, insert into right subtree
    else
        root->right = insert(root->right, value);

    return root; // return unchanged root
}

// Inorder traversal (Left → Root → Right)
void inorder(struct node* root) {

    // recursion stops when node becomes NULL
    if (root != NULL) {

        inorder(root->left);          // visit left subtree
        printf("%d ", root->data);    // print current node
        inorder(root->right);         // visit right subtree
    }
}

int main() {

    struct node* root = NULL;

    // inserting given elements into BST
    root = insert(root, 50);
    insert(root, 30);
    insert(root, 70);
    insert(root, 20);
    insert(root, 40);
    insert(root, 60);
    insert(root, 80);

    printf("Inorder Traversal: ");
    inorder(root);   // perform traversal

    return 0;
}

Output

Inorder Traversal: 20 30 40 50 60 70 80


---

2. C program to create a binary tree and count total nodes using recursion

Tree structure used:

10
     /  \
   20    30
  /  \
40   50

#include <stdio.h>
#include <stdlib.h>

// Node structure
struct node {
    int data;
    struct node *left;
    struct node *right;
};

// Function to create node
struct node* createNode(int value) {

    struct node* newNode = (struct node*)malloc(sizeof(struct node));

    newNode->data = value;   // assign value
    newNode->left = NULL;    // initialize left child
    newNode->right = NULL;   // initialize right child

    return newNode;
}

// Recursive function to count nodes
int countNodes(struct node* root) {

    // Base condition: if tree is empty
    if (root == NULL)
        return 0;

    // count = left subtree + right subtree + current node
    return 1 + countNodes(root->left) + countNodes(root->right);
}

int main() {

    // Manually creating the given binary tree
    struct node* root = createNode(10);

    root->left = createNode(20);
    root->right = createNode(30);

    root->left->left = createNode(40);
    root->left->right = createNode(50);

    // Calling recursive function
    int total = countNodes(root);

    printf("Total number of nodes = %d", total);

    return 0;
}

Output

Total number of nodes = 5


---

3. C program to create a binary tree and find the height of the tree

Tree structure used:

15
 |
25
 |
35
 |
45

#include <stdio.h>
#include <stdlib.h>

// Node structure
struct node {
    int data;
    struct node *left;
    struct node *right;
};

// Function to create node
struct node* createNode(int value) {

    struct node* newNode = (struct node*)malloc(sizeof(struct node));

    newNode->data = value;  // assign value
    newNode->left = NULL;   // initialize children
    newNode->right = NULL;

    return newNode;
}

// Function to find height using recursion
int height(struct node* root) {

    // if tree is empty
    if (root == NULL)
        return 0;

    // find height of left subtree
    int leftHeight = height(root->left);

    // find height of right subtree
    int rightHeight = height(root->right);

    // return greater height + 1 for current node
    if (leftHeight > rightHeight)
        return leftHeight + 1;
    else
        return rightHeight + 1;
}

int main() {

    // creating the given tree
    struct node* root = createNode(15);
    root->left = createNode(25);
    root->left->left = createNode(35);
    root->left->left->left = createNode(45);

    int h = height(root);

    printf("Height of tree = %d", h);

    return 0;
}

Output

Height of tree = 4
