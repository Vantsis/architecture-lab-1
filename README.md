Exercise 1
In a course taught at a university, the final grade is derived from grade a of the final examination, which is an integer between 0 and 100, and the grade of laboratory b, which is an integer between 0 and 20.
To calculate the final grade, which is an integer between 0 and 100, first calculate the total grade c, which is the integer part of the expression 8a / 10 + b. The following cases are distinguished:
• if c is greater than 47 and a is not greater than 47, then the final score is 47.
• if c and a are greater than 47 and c is less than 50, then the final score is 50.
• In any other case the final grade is equal to the total grade c.
Write a grade function in Haskell that will accept the final exam and lab scores as arguments and return the final grade. The type of the function should be Int-> Int-> Int. If either argument has an unacceptable value, then the grade function must return the value -1.
Use the following values to check:
Main> grade 100 20 
100 
Main> grade 100 0
 80 
Main> grade 0 20 
20 
Main> grade 80 20 
84
 Main> grade 59 10 
57 
Main> grade 48 10 
50 
Main> grade 48 9 
47 
Main> grade 40 20 
47 
Main> grade 20 100
 -1 
Main> grade 35 (-2) 
-1

Exercise 2
In a gambling every Saturday an 8-digit lucky number is drawn between 10000000 and 99999999. παί A player who has bet on a number, wins an amount that depends on the number of digits of that number which are identical to the digits of the lucky number in the corresponding positions, according to the following table:
	Digits that agree	Amount the player wins 
 Write a digits function in Haskell which will take as arguments the lucky number and the number that a player has chosen and will calculate the amount that the player wins. The type of the function should be Int-> Int-> Int. You can assume that the two arguments are always eight-digit numbers.
Use the following values to check:
Main> digits 13758455 13758455 
1000000 
Main> digits 22812509 22852509 
100000 
Main> digits 38954421 70954421 
8000 
Main> digits 42358921 42358002 
300 
Main> digits 12548706 14520786 
20 
Main> digits 80000012 71800009
5 
Main> digits 42212553 22125531 
1 
Main> digits 58723493 83463738 
0 
Main> digits 78354623 46237835 
0 
Main> digits 34578364 83648364 
20

