![image](https://github.com/user-attachments/assets/0dd14449-68d0-4f9b-9a61-4908819f3404)## Infix to Postfix Conversion with Subtraction and Multiplication Using Dictionary and Set

## Aim:
To convert an infix expression to postfix expression by following precedence and associativity rules using a dictionary for operator priority and a set to hold operators.
## Procedure:

1.Define operator precedence using a dictionary.

2.Store valid operators in a set.

3.Initialize an empty stack for operators and an empty list for the result.

4.Traverse each character in the infix expression:
 • If it’s an operand, add to result.

 • If it’s an operator, pop operators from the stack to result until stack is empty or top has lower precedence, then push current operator.

 • Handle parentheses if included.
  

5.Pop remaining operators from the stack to result.

6.Display the resulting postfix expression.

## Program:
```
operators = set(['-', '*'])
priority = {'-': 1, '*': 2}

def infixToPostfix(expression):
    stack = []
    output = ''
    
    for char in expression:
        if char.isnumeric():
            output += char
        elif char in operators:
            while stack and stack[-1] in operators and priority[char] <= priority[stack[-1]]:
                output += stack.pop()
            stack.append(char)
        elif char == '(':
            stack.append(char)
        elif char == ')':
            while stack and stack[-1] != '(':
                output += stack.pop()
            stack.pop()
    
    while stack:
        output += stack.pop()
    
    return output

expression = input()
print("infix notation: ", expression)
print("postfix notation: ", infixToPostfix(expression))



```
## Output

![Screenshot 2025-04-07 091736](https://github.com/user-attachments/assets/0b119945-fbd2-4038-8ef1-3a5fba656114)



## Result:
Successfully converted an infix expression with subtraction and multiplication into postfix notation using a dictionary for precedence and a set for operator validation.
