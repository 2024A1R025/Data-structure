#include <stdio.h>
#include <string.h>
#include <ctype.h>
#include <math.h>
#define SIZE 100
int top1 = -1, top2 = -1;
int operand[SIZE];
char operator[SIZE];
int precedence(char operator){
    return (operator == '+' || operator == '-') ? 1 : (operator == '*' || operator == '/') ? 2 : (operator == '^') ? 3 : 0;
}
void doProcess()
{
    if (top1 < 1 || top2 < 0)
        return;
    int x = operand[top1--];
    int y = operand[top1--];
    char oper = operator[top2--];
    int z;
    switch (oper)
    {
    case '+':
        z = y + x;
        break;
    case '-':
        z = y - x;
        break;
    case '*':
        z = y * x;
        break;
    case '/':
        z = y / x;
        break;
    case '^':
        z = (int)pow(y, x);
        break;
    }
    operand[++top1] = z;
}

int evalInfix(char *exp)
{
    int size = strlen(exp);
    for (int i = 0; i < size; i++)
    {
        char ch = exp[i];
        if (isspace(ch))
            continue; // Ignore spaces
        if (isdigit(ch))
        {
            int num = 0;
            while (isdigit(exp[i]))
            {
                num = num * 10 + exp[i] - 48;
                i++;
            }
            i--;
            operand[++top1] = num; // Push the number onto the operand stack
        }
        else if (ch == '+' || ch == '-' || ch == '*' || ch == '/' || ch == '^')
        {
            if (top2 == -1)
                operator[++top2] = ch;
            else
            {
                while (top2 != -1 && precedence(ch) <= precedence(operator[top2]))
                {
                    doProcess();
                }
                operator[++top2] = ch;
            }
        }
        else if (ch == '(')
        {
            operator[++top2] = '(';
        }
        else if (ch == ')')
        {
            while (operator[top2] != '(')
            {
                doProcess();
            }
            top2--;
        }
    }
    while (top2 >= 0)
    { // Process remaining operators until stack becomes empty
        doProcess();
    }
    return operand[top1];
}
int evalPreFix(char* exp){
    int size = strlen(exp);
    for (int i = size-1; i >= 0; i--){
        char ch = exp[i];
        if (isdigit(ch)){
            int num = 0;
            while (isdigit(exp[i])){
                num = num*10 + exp[i] - '0';
                i++;
            }
            i--;
            operand[++top1] = num;
        }
        else if (ch == '+' || ch =='-' || ch == '*' || ch == '/' || ch == '^'){
            int x = operand[top1--];
            int y  = operand[top1--];
            int z;
            switch (ch){
                case '+':
                    z= y+x; break;
                case '-':
                    z = y-x; break;
                case '*':
                    z = y*x; break;
                case '/':
                    z = y/x; break;
                case '^':
                    z = y^x; break;
                }
            operand[++top1] = z;
        }
    }
    return operand[top1--];
}
int evalPostFix(char* exp){
    int size = strlen(exp);
    for (int i = 0; i < size; i++){
        char ch = exp[i];
        if (isdigit(ch)){
            int num = 0;
            while (isdigit(exp[i])){
                num = num*10 + exp[i] - '0';
                i++;
            }
            i--;
            operand[++top1] = num;
        }
        else if (ch == '+' || ch =='-' || ch == '*' || ch == '/' || ch == '^'){
            int x = operand[top1--];
            int y  = operand[top1--];
            int z;
            switch (ch){
                case '+':
                    z= y+x; break;
                case '-':
                    z = y-x; break;
                case '*':
                    z = y*x; break;
                case '/':
                    z = y/x; break;
                case '^':
                    z = y^x; break;
            }
            operand[++top1] = z;
        }
    }
    return operand[top1--];
}

int main() {
    char str[100];
    printf("Enter infix expression: ");
    fgets(str, 100, stdin);
    printf("Result (Infix): %d\n", evalInfix(str));
    
    printf("Enter postfix expression: ");
    fgets(str, 100, stdin);
    printf("Result (Postfix): %d\n", evalPostFix(str));
    
    printf("Enter prefix expression: ");
    fgets(str, 100, stdin);
    printf("Result (Prefix): %d\n", evalPreFix(str));
    
    return 0;
}
