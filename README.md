# Lecture 1 (Introduction to Cryptography)

Refrences - https://www.youtube.com/watch?v=2aHkqB2-46k&t

![p1](./p1.png)

Crytpanalysis is more towards hacker point of view.

## Can you make your own Cryptographic function?
if we have to make our own cryptographic function , no matter how many matrix , trignomentery or logic we should use , there is a 99% chance that what we make is pretty hackable.

### So how people make cryptographic function?
they just make it , and prays that nobody is able to hack it , if it is unhackable for about 5-10 years then it is geral assumption that it is unhackable.
........So basically we are just hitting a blank in a sky .

![p2](./p2.png)

## Notation
<li>X = PlainText</li>
<li>Y = cipherText</li>
<li>E = encrytion</li>
<li>D =  decrytion</li>
<li>k = Key</li>
<li>|k| = Key set</li>



## kirchhoff principle cryptography

A good cryptographic system should remain secure even if the algorithm used is known.


## Subsitution cipher 

- old and stupid cipher ......jo 100 saal se chle jaa rhe 
- basically they operates on plain text letter

example -
```
A ko d bna do
B -> l
C -> k
```


### Is this Secure ??
no..

### Can we attack the cipher ?

#### Brute force .
- total 26 letter
- if one letter is using k for C.....26 remnong are 25 .....
- so 26! is the answer 
-- it is still the big answer


#### Letter frequecy annalysis

![p3](./p3.png)


basically we find which letter in encryted text is most and then try to match it with usually highest alabhaptes in english

## types of attacks in cytoanalysis
![p4](./p4.png)






