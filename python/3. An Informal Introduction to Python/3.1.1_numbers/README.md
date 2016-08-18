# 3.1.1. Numbers

The interpreter acts as a simple calculator: you can type an expression at it and it will write the value. Expression syntax is straightforward: the operators +, -, * and / work just like in most other languages (for example, Pascal or C); parentheses (()) can be used for grouping. For example:
>>>

>>> 2 + 2
4
>>> 50 - 5*6
20
>>> (50 - 5.0*6) / 4
5.0
>>> 8 / 5.0
1.6

The integer numbers (e.g. 2, 4, 20) have type int, the ones with a fractional part (e.g. 5.0, 1.6) have type float. We will see more about numeric types later in the tutorial.

The return type of a division (/) operation depends on its operands. If both operands are of type int, floor division is performed and an int is returned. If either operand is a float, classic division is performed and a float is returned. The // operator is also provided for doing floor division no matter what the operands are. The remainder can be calculated with the % operator:
>>>

>>> 17 / 3  # int / int -> int
5
>>> 17 / 3.0  # int / float -> float
5.666666666666667
>>> 17 // 3.0  # explicit floor division discards the fractional part
5.0
>>> 17 % 3  # the % operator returns the remainder of the division
2
>>> 5 * 3 + 2  # result * divisor + remainder
17

With Python, it is possible to use the ** operator to calculate powers [1]:
>>>

>>> 5 ** 2  # 5 squared
25
>>> 2 ** 7  # 2 to the power of 7
128

The equal sign (=) is used to assign a value to a variable. Afterwards, no result is displayed before the next interactive prompt:
>>>

>>> width = 20
>>> height = 5 * 9
>>> width * height
900

If a variable is not “defined” (assigned a value), trying to use it will give you an error:
>>>

>>> n  # try to access an undefined variable
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'n' is not defined

There is full support for floating point; operators with mixed type operands convert the integer operand to floating point:
>>>

>>> 3 * 3.75 / 1.5
7.5
>>> 7.0 / 2
3.5

In interactive mode, the last printed expression is assigned to the variable _. This means that when you are using Python as a desk calculator, it is somewhat easier to continue calculations, for example:
>>>

>>> tax = 12.5 / 100
>>> price = 100.50
>>> price * tax
12.5625
>>> price + _
113.0625
>>> round(_, 2)
113.06

This variable should be treated as read-only by the user. Don’t explicitly assign a value to it — you would create an independent local variable with the same name masking the built-in variable with its magic behavior.

In addition to int and float, Python supports other types of numbers, such as Decimal and Fraction. Python also has built-in support for complex numbers, and uses the j or J suffix to indicate the imaginary part (e.g. 3+5j).