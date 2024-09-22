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
```a. a^-1 ≡ 1 mod m ```
 if an inverse exist for a we can  divide by the elements since ```b/a = b -a^-1```
 - it takes some effort to find inverse

 ### how to know if inverse exist for current Equation
 **Q**  ```6 . ? ≡ 1 mod 9```
 - find gcd(6,9) =3
 - if gcd is not equal to 1 then inverse does not exist

## Shift cipher

