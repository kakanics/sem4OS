# Lab 4

## Task 1

**Part a**

This script takes three command-line arguments and determines which one is the greatest.

```bash
#!/bin/bash

if [ $1 -gt $2 -a $1 -gt $3 ]; then
    echo $1 is greatest
elif [ $2 -gt $3 -a $2 -gt $1 ]; then
    echo $2 is greatest
else
    echo $3 is greatest
fi
```

**Part b**
This script uses a `case` statement to determine the day of the week based on the output of the `date` command.

```bash
#!/bin/bash

day=$(date +%A)
case $day in
    Monday) echo Monda ;;
    Tuesday) echo tues ;;
    Wednesday) echo wed ;;
    Thursday) echo thurs ;;
    Friday) echo fri ;;
    Saturday) echo sat ;;
    Sunday) echo sun ;;
esac
```

## Task 2

**Part 2a**
This script uses a `for` loop to iterate over the numbers from 1 to 10. For each number, it checks whether the number is even or odd using
arithmetic expressions.

```bash
#!/bin/bash

for i in {1..10}; do
    if [ $(( i % 2 )) -eq 0 ]; then
        echo $i is even
    else
        echo $i is odd
    fi
done
```

**Part 2b**
This script asks the user to enter a number, and then calculates the sum of the digits of that number using a `while` loop.

```bash
#!/bin/bash

echo enter a number
read input

y=10
sum=0

while [ $(( input % y )) -gt 0 ]; do
    sum=$(( sum + input % y))
    input=$(( input / 10 ))
done

echo $sum
```

## Task 3

**Part 3a**
This script defines two functions: `reverse` and `palindromeCheck`. The `reverse` function takes a number as input, reverses its digits
using a `while` loop, and then calls the `palindromeCheck` function to check whether the original number is the same as the reversed one.

```bash
#!/bin/bash

reverse() {
    newNum=0
    oldNum=$1
    while [ $oldNum -gt 0 ]; do
        newNum=$(( newNum * 10 ))
        newNum=$(( newNum + oldNum%10 ))
        oldNum=$(( $oldNum/10 ))
    done
    palindromeCheck $1 $newNum
}

palindromeCheck() {
    echo palindromeChecker Started
    if [ $1 -eq $2 ]; then
        echo is a palindrome
    else
        echo not a palindrome
    fi
    echo palindromeChecker completed
}

reverse $1
```

**Part 3b**
This script defines a function `factorial` that calculates the factorial of a given number using recursion.

```bash
#!/bin/bash

factorial() {
    if [ $1 -eq 0 ]; then
        echo 1
    else
        echo $(($1 * $(factorial $(( $1 - 1 )))))
    fi
}

x=$(factorial 5)
echo $x
```
