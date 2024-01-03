---------------------------
-- Exercise 1
---------------------------

grade :: Int -> Int -> Int
grade a b
    -- If either number is out of bounds then the result is -1
    | (a < 0) || (a > 100)        = -1
    | (b < 0) || (b > 20)         = -1
    -- These are the conditions of the problem.
    | c > 47 && a <= 47           = 47
    | c > 47 && a > 47  && c < 50 = 50 
    | otherwise                   = c
        where
            -- c = 8a/10 + b, associativity is important since we are using integer division.
            c =  (8*a) `div` 10 + b 


---------------------------
-- Exercise 2
---------------------------

-- Works for any number of digits.
digits :: Int -> Int ->  Int
-- in order to give the answer, we find how many digits match and we apply the prize function to the result.
digits x = prize . digits' x

-- An auxiliary function that counts the number of digits that matches.
digits' :: Int -> Int ->  Int
-- Since the number is non-zero, then this match should always yield 0
-- instead of: if y == 0 then 1 else 0
digits' 0 _    = 0
-- same as before
digits' _ 0    = 0
digits' x  y
    -- if we take mod x 10, this yields the least significant digit of x: mod 153 10 = 3
    -- and if we do: div x 10, this will drop the least significant digit: 153 `div` 10 = 15
    -- therefore, in every iteration we are checking if the least significant digits match,
    -- if they do, we add 1 and proceed to next iteration, if they don't, we proceed to the next interation.
    -- the next iteration is doing the same but forgetting (dividing by 10) the least significant digit.
    | mod x 10 == mod y 10 = 1 + digits' (x `div` 10) (y `div` 10)
    | otherwise            = digits' (x `div` 10) (y `div` 10)

-- Just the table of prices
prize :: Int -> Int
prize 7 = 100000
prize 6 = 8000
prize 5 = 300
prize 4 = 20
prize 3 = 5
prize 2 = 1
prize n
    -- in case that we want to generalize to more than 8 digit numbers, we consider that the maximum prize is always 1000000.
    | n >= 8 = 1000000
    | n < 2  = 0