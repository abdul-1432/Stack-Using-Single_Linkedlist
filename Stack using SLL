#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *link;
};

struct node *first = NULL;

void insert_node(int value) {
    struct node *newNode = (struct node *)malloc(sizeof(struct node));
    newNode->data = value;
    newNode->link = NULL;

    if (first == NULL) {
        first = newNode;
    } else {
        struct node *current = first;
        while (current->link != NULL) {
            current = current->link;
        }
        current->link = newNode;
    }
}

void delete_node(int value) {
    struct node *temp = first;
    struct node *prev = NULL;

    if (temp != NULL && temp->data == value) {
        first = temp->link;
        free(temp);
        return;
    }

    while (temp != NULL && temp->data != value) {
        prev = temp;
        temp = temp->link;
    }

    if (temp == NULL) {
        printf("Element not found in the list.\n");
        return;
    }

    prev->link = temp->link;
    free(temp);
}

void reverse_list_recursive(struct node *current, struct node *prev) {
    if (current->link == NULL) {
        first = current;
        current->link = prev;
        return;
    }

    struct node *next = current->link;
    current->link = prev;
    reverse_list_recursive(next, current);
}

void reverse_list() {
    if (first == NULL) {
        printf("List is empty.\n");
        return;
    }

    reverse_list_recursive(first, NULL);
}

void display_list() {
    if (first == NULL) {
        printf("List is empty.\n");
        return;
    }

    struct node *temp = first;
    printf("Linked List values are: ");
    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->link;
    }
    printf("\n");
}

int main() {
    int choice, value;

    while (1) {
        printf("\n*** Single Linked List Operations ***\n");
        printf("1. Insert Node\n");
        printf("2. Delete Node\n");
        printf("3. Reverse List\n");
        printf("4. Display List\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter the value to insert: ");
                scanf("%d", &value);
                insert_node(value);
                break;
            case 2:
                printf("Enter the value to delete: ");
                scanf("%d", &value);
                delete_node(value);
                break;
            case 3:
                reverse_list();
                printf("List reversed successfully.\n");
                break;
            case 4:
                display_list();
                break;
            case 5:
                printf("Exiting...\n");
                exit(0);
            default:
                printf("Invalid choice! Please try again.\n");
        }
    }

    return 0;
}
