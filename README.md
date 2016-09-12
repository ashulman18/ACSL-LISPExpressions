# ACSL-LISPExpressions

PROBLEM: Given a valid arithmetic LISP expression that contains an operator followed by 1 or more sublists, 
perform string operations on the expression. There will be a single space between every operation and the 
numbers used for that operation. There will be no space after a left parenthesis or before a right parenthesis. 
The entire expression must be inputted as a single string. The operators used will be ADD, SUB, MULT, DIV, SQR,
and EXP. Sample LISP expressions could include:

(SQR (MULT 3 4 5))
(MULT (DIV 20 4) (EXP -2 3))
(DIV (ADD 5 4 -6 7) (MULT 3 -1 7) (SUB 5 4))

INPUT: There will be 6 lines of input. The first line will contain a valid arithmetic LISP expression. We guarantee that it will have no more than 2 levels of parentheses. The following 5 lines will contain a command from the following list:

COUNT: Print the number of sublists in the given expression.
REMOVE J K: Print the expression that results when the elements between the Jth and Kth sublists inclusive are eliminated. J and K will be positive integers in increasing order.
SORT J K: Print the expression that results when the elements between the Jth and Kth sublists inclusive are sorted alphabetically based on their operation. J and K will be positive integers in increasing order.
REVERSE J K:Print the expression that results when the elements between the Jth and Kth sublists inclusive are reversed. J and K will be positive integers in increasing order.
MAXIMUM: Print the sublist with the most arguments.

This is for the ACSL Senior Division Contest 2 2014-2015
