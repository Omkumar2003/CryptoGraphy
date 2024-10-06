# Lecture 1 (Introduction to Cryptography)

Refrences - https://www.youtube.com/watch?v=2aHkqB2-46k&t

**what we are going to study in this chapter**
```
classicfication
basics/setup
subsitution cipher
attacks
```
## Classicfication
 modern application of Cryptography
  - gnu pg
  - secureshell
  - (plug-in) for thunderbird
  - s-MIME email encryption
  - cell phone
  - hdcp -multimedia protocol
  - bank cards
  - VPN
  - E-passport
  - online- banking
  - Ipod
  - kindle

![ch_1_1](./ch_1_1.png)

## Basics
![ch_1_2](./ch_1_2.png)
- channel example - Internet , airwaves , Gsm , Wifi

```
+-------------+---------------------+
| SHORT FROMS |       MEANING       |
+-------------+---------------------+
|      x      |      plain text     |
+-------------+---------------------+
|      y      |     cipher text     |
+-------------+---------------------+
|      e      | encryption function |
+-------------+---------------------+
|      d      | decryption function |
+-------------+---------------------+
|      k      |         key         |
+-------------+---------------------+
|     |k|     |      key space      |
+-------------+---------------------+
```

### Kerchoffs principle [1883]

A crypto system should be secured even if the attacker(Oscor) knows all the details about the system with the exception of the secret key.

## Subsitution Cipher
 - historical cipher
 - operates on letters
 - **Idea** - Replace every plaintext letter by a fixed ciphertext letter

 - **example**  - A -> l , B-> d , C -> w , and so on
 ```
 e(ABBA) -> lddl
 ```
### Is this cipher secure ?
NO
## How can we Attack the cipher ?

### Brute Force/Exhaustive key search

```
26 * 25 * 24 ... * 1 = 26!
```

key space is too large

### frequency analysis
we will guess which letter is which 
![ch_1_3](./ch_1_3.png)


# Lecture 2

**what we are going to study in this chapter**
```
modular arithmetic
rings
shift cipher
affine
```

## Modular arithmetic

**Goal** - Computation in finite set
**Example** - Clock, angles

### Defination of modulo operator

let ```a, r, m ∈ z```   and  ``` m > 0```

then we write ``` a = r mod m```
only if ```m divides (a-r)``` OR ```m / (a-r)``` 

**The r(remainder is not unique)**

**Syntax**  ``` a = r mod m```
### Q. 12 = **?** mod 5

```
+--------------------------------------------+---------------+
| First Check if it is divisible -> m /(a-r) |    Equation   |
+--------------------------------------------+---------------+
|                 5 / (12-2)                 |  12 ≡ 2 mod 5 |
+--------------------------------------------+---------------+
|                 5 / (12-7)                 |  12 ≡ 7 mod 5 |
+--------------------------------------------+---------------+
|               5 / (12 -(-3))               | 12 ≡ -3 mod 5 |
+--------------------------------------------+---------------+
|                      .                     |       .       |
+--------------------------------------------+---------------+
|                      .                     |       .       |
+--------------------------------------------+---------------+
|                      .                     |       .       |
+--------------------------------------------+---------------+
```

- so remainders can be 2 , 7 , -3 .....WAIT A MINUTE 
- THERE IS PATTERN ```{..., -8, -3, 2, 7, 12,...  }```
- it forms an equivalence class of modulos 5.(It is just 1 class from the total 5 class ....5 bcoz modulo 5) 
- **All equivalence classes of modulo 5**
```
{..., -10, -5, 0, 5, 10,...  }
{..., -9, -4, 1, 6, 11,...  }
{..., -8, -3, 2, 7, 12,...  }
{..., -7, -2, 3, 8, 13,...  }
{..., -6, -1, 4, 9, 14,...  }

```

**if in last we have to do modulo we can write that big number to the small number from the modulo equivalence class table**

**Example** - ``(13*6 -8) mod 5     ->    (3*1 -3)=0  ``


## Rings 

Here are some rules for rings
- we can add and multiply any two number and the result is always in the ring then the ring is set to be **closed** 
- addition and multiplication of are **associative**
``a+(b+c) = (a+b)+c```
- there is the **neutral element 0 with respect to addition** which holds
 ```a+0 ≡ a mod m```
- for any element a in the ring there is always the negative element a which we call additive inverse 
```a +(-a) ≡ 0 mod m```
- **neutral element with respect to  multiplication**
```a * 1 ≡ a mod m```
- **multiplicative inverse exist only for some not for all**
```a. a⁻¹ ≡ 1 mod m ```
 if an inverse exist for a we can  divide by the elements since ```b/a = b -a⁻¹```
 - it takes some effort to find inverse

 ### how to know if inverse exist for current Equation
 **Q**  ```6 . ? ≡ 1 mod 9```
 - find gcd(6,9) =3
 - if gcd is not equal to 1 then inverse does not exist

## Shift cipher

```
+----------+----------------------------+
| albhabet | number related to alphabet |
+----------+----------------------------+
|     a    |              0             |
+----------+----------------------------+
|     b    |              1             |
+----------+----------------------------+
|     c    |              2             |
+----------+----------------------------+
|     d    |              3             |
+----------+----------------------------+
|     e    |              4             |
+----------+----------------------------+
|     f    |              5             |
+----------+----------------------------+
|     g    |              6             |
+----------+----------------------------+
|     h    |              7             |
+----------+----------------------------+
|     i    |              8             |
+----------+----------------------------+
|     j    |              9             |
+----------+----------------------------+
|     k    |             10             |
+----------+----------------------------+
|     l    |             11             |
+----------+----------------------------+
|     m    |             12             |
+----------+----------------------------+
|     n    |             13             |
+----------+----------------------------+
|     o    |             14             |
+----------+----------------------------+
|     p    |             15             |
+----------+----------------------------+
|     q    |             16             |
+----------+----------------------------+
|     r    |             17             |
+----------+----------------------------+
|     s    |             18             |
+----------+----------------------------+
|     t    |             19             |
+----------+----------------------------+
|     u    |             20             |
+----------+----------------------------+
|     v    |             21             |
+----------+----------------------------+
|     w    |             22             |
+----------+----------------------------+
|     x    |             23             |
+----------+----------------------------+
|     y    |             24             |
+----------+----------------------------+
|     z    |             25             |
+----------+----------------------------+
```

**encryption : eₖ(x) ≡ x + k mod 26**

**decryption : dₖ(y) ≡ y - k mod 26**

Example-
 ```
 "attack" word
                attack              ->      0 19 19 0 2 10 
 key -> 17
                17 10 10 17 19 1     ->     rkkrtb

```

### two possible attacks
- brute Force
- frequency analysis

## Affine cipher
- key is divided in 2 parts
- affine cipher is a Better version of shift cipher
- the affine encrypts by multipliying the plain text by one out of the key followed by the addition of the another part of the key

```k = (a,b)```

**encryption** ```y ≡ a.x + b mod 26 ```

**decryption** ```x ≡ a⁻¹ + (y-b) mod 26 ```

|k| = |a| * |b|

we can only use a when ```gcd(a,26)=1```
so total space are```{1,3,5,7,9,11...}``` total element = 12

b space = 26 (26 letters)

so **|k| = 12*36 = 312**

### attack
- brute Force
- frequency analysis






# Lecture 3
**what we are going to study in this chapter**
```
Stream cipher
Random number
OTP 
LCR 
```

## Stream cipher

A stream cipher encrypts bits individually.

- **encryption** ```yᵢ = e(xᵢ)  ≡ xᵢ + sᵢ mod 2```
- **decryption** ```xᵢ = d(yᵢ)  ≡ yᵢ + sᵢ mod 2```
 
### Why mod 2 is there?
**Because the answer should be in 0 or 1**


 ### Why in both encryption and decryption there is an addition symbol ? doesn't it make sense to put plus in an encryption and minus in decryption or vice- versa?

 **I remind you the definition of stream cypher is encrypting bits individually and when encrypting bits individually it does not matter if we use addition or subtraction because at Binary level addition and Subtraction are the same operation**
![ch_3_1](./ch_3_1.png)

 ## closer look at mod 2 

 ```
 +----+----+----+
| xᵢ | sᵢ | Yᵢ |
+----+----+----+
| 0  | 0  | 0  |
| 0  | 1  | 1  |
| 1  | 0  | 1  |
| 1  | 1  | 0  |
+----+----+----+
 ```
**Mod 2 Adition is same as XOR operation**

## Now we know how to encrypt and decrypt but there is still 1 thing missing which is how to generate the key stream bits  sᵢ ?

**Somehow this question is related to randomness**
![ch_3_2](./ch_3_2.png)
### TRNG (true random number generator)

True random numbers come from physical processes 
EXMAPLE - Coin flipping, lottery, noise, thermal, mouse movement ,keystroke timing

### PRNG (pseudo random number generator)

- PRMG are computed
- They are deterministic 
- often they are computed with the help of following function
```
Sᵢ₊₁ = f(sᵢ)

where S₀ Comes from another source or you can say it is a true Random generator
```
Carefully see that only the first thing will be random and all the other iterations or subsequent iteration can be found with the help of the previous one

### CPRNG (cryptographically secure PRNG)
Cprng rprng with an additional property the numbers are **unpredictable**

```
Given n output bits

Sᵢ , Sᵢ₊₁ , . . . , Sᵢ₊₍ₙ₋₁₎

Then it is computationally infeasible to construct Sₙ
```


## OTP (one time pad)

It is not that OTP which you are thinking about.......


So what actually do we have learnt and what is our goal?

**Our goal is to make a perfect cypher which no one can break it**

A cypher is unconditionally secure (or information theoretical secure) if it cannot be broken even with the infinite computing resources then it is said to be a perfect cypher.

### What is OTP?

- It is a stream cypher
- The keystream bits are from TRNG
- Each keystream bit is used only once

**Big drawback is that he is as long as the message........... Yes it is secure but it can cost a lot time as well as money as well as space**


## LCG (Linear congruential generator)
![ch_3_3](./ch_3_3.png)
- So the idea is use the key screen si from prng

```
Sᵢ₊₁ = A . Sᵢ + B mod m 

where A, B, Sᵢ belongs Finite set of integer

So key     k = (A,B)
```

