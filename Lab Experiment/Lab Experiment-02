#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <limits.h>
#define MAX_SIZE 100
int stack[MAX_SIZE], top = -1;

bool isEmpty(){
    return top == -1;
}
bool isFull(){
    return top == MAX_SIZE-1;
}
void push(int value){
    if (!isFull()){
        stack[++top]= value;
        printf("Element Added\n");
    } else {
        printf("Stack Overflow!!");
    }
}
int pop(){
    if (!isEmpty()){
        int a = stack[top];
        stack[top--]= 0;
        return a;
    } else {
        printf("Stack Underflow");
        return INT_MIN;
    }
}
void show(){
    if (isEmpty()){
        printf("Stack is empty\n");
    } else {
        printf("Stack elements are: \n");
        for (int i = top; i >= 0; i--){
            printf("%d\n", stack[i]);
        }
        printf("\n");
    }
}


int main(){
    while (1){
        printf("1. Push 2. Pop 3. Show 4. Exit\n");
        int choice;
        printf("Enter your choice: "); scanf("%d",&choice);
        switch(choice){
            case 1:
            {
                int val; printf("Enter Value : ");
                scanf("%d",&val);
                push(val);
                break;
            }
            case 2:{ 
                int a = pop();
                if (a!= INT_MIN)
                    printf("%d popped from Stack\n", a);
                break;
            }
            case 3:
            show();
                break;
            case 4:
                exit(0);
            default:
                printf("Invalid Choice!!\n");
        }
        system("pause"); printf("\n");
    }
}
