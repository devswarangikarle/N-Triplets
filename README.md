# N-Triplets

Alisha is still not satisfied with Harsh's math skills so she gave him a new challenge.
Given a positive integer N, find any 3 distinct positive integers A, B, C such that:
The product of any two of these 3 integers is a divisor of N.
The product of all three integers is a multiple of N.
If multiple solutions exist, you may print any of them. Print -1 if no solution exists.

def find_divisors(n):

    divisors = []
    for i in range(1, int(n**0.5) + 1):
        if n % i == 0:
            divisors.append(i)
            if i != n // i:
                divisors.append(n // i)
    return sorted(divisors)

def find_triplet(n):

    divisors = find_divisors(n)
    if len(divisors) < 3:
        return -1
    for i in range(len(divisors)):
        for j in range(i + 1, len(divisors)):
            for k in range(j + 1, len(divisors)):
                A, B, C = divisors[i], divisors[j], divisors[k]
                if (A * B) % n == 0 and (A * C) % n == 0 and (B * C) % n == 0 and (A * B * C) % n == 0:
                    return A, B, C
    return -1

T = int(input())  
for _ in range(T):
    N = int(input()) 
    result = find_triplet(N)
    if result == -1:
        print(-1)
    else:
        print(*result)
