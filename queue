#include <stdio.h>
#include <stdlib.h>

typedef struct Task {
    char name[50];
    char priority[10];
    int totalTime;
    int remainingTime;
} Task;

typedef struct Node {
    Task task;
    Node* next;
} Node;

typedef struct Queue {
    Node* first;
    Node* last;
} Queue;

Node* createNode(Task task) {
    Node* newNode = (Node*)malloc(sizeof(Node));
    newNode->task = task;
    newNode->next = NULL;
    return newNode;
}

Queue* createQueue() {
    Queue* newQueue = (Queue*)malloc(sizeof(Queue));
    newQueue->first = NULL;
    newQueue->last = NULL;
    return newQueue;
}

void queueUp(Queue* queue, Task task) {
    Node* newNode = createNode(task);

    if (queue->last == NULL) {
        queue->first = newNode;
        queue->last = newNode;
    } else {
        queue->last->next = newNode;
        queue->last = newNode;
    }
}

Task queueDown(Queue* queue) {
    Node* temp = queue->first;
    Task removedTask = temp->task;
    queue->first = queue->first->next;
    return removedTask;
}


void showQueue(Queue* queue, const char* queueType) {
    Node* current = queue->first;
    printf("%s:\n", queueType);
    while (current != NULL) {
        printf("%s, Priority: %s, Total Time: %d, Remaining Time: %d\n",
               current->task.name, current->task.priority, current->task.totalTime, current->task.remainingTime);
        current = current->next;
    }
}

int main() {
    Queue* importantQueue = createQueue();
    Queue* otherQueue = createQueue();

    Task task1 = {"Learn C 1", "High", 10, 9};
    Task task2 = {"Learn C 2", "High", 10, 9};
    Task task3 = {"Learn C 3", "High", 10, 9};
    Task task4 = {"Learn C++ 1", "Other", 10, 9};
    Task task5 = {"Learn C++ 2", "Other", 10, 9};
    Task task6 = {"Learn C++ 3", "Other", 10, 9};

    queueUp(importantQueue, task1);
    queueUp(importantQueue, task2);
    queueDown(importantQueue);
    queueUp(importantQueue, task3);
    queueUp(otherQueue, task4);
    queueUp(otherQueue, task5);
    queueUp(otherQueue, task6);

    showQueue(importantQueue, "Important");
    showQueue(otherQueue, "Other");

    return 0;
}
