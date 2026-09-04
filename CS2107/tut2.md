# CS2107 Tutorial 2

## Question 1, hint same IV

### Analysis

Since the qn hints the use of same IV, $C_1 = IV \oplus  P_x$ and $C_2 = IV \oplus P_y$ then $C_1 \oplus C_2 = P_x \oplus IV \oplus P_y \oplus IV = P_x \oplus P_y$

### Code

```python
C1 = 0b011111011011
C2 = 0b011100101011
P1 = 0b00000000
P2 = 0b11111111
P3 = 0b00001111
P4 = 0b11000011
flag = C1 ^C2
temp = [P1, P2, P3, P4]

for i in range(len(temp)//2 + 1):
    for j in range(i + 1, len(temp)):
        if temp[i] ^ temp[j] == flag:
            print(f"plaintexts P{i + 1} and P{j + 1}")
            break
```

## Question 2, Meet in the middle

### Analysis

Applied DES 4 time with 4 unique 56 bits keys, and hint is to use meet in the middle.

1st pair of keys, ($2^{56}$) cases to consider

2nd pair of keys, same as the above

As such, total cases to consider is $(2^{56})^2 \cdot 2 = 2^{113}$

## Question 3 insecure IV implementation, length reveals information

User can either buy / sell / sell everything / hold and see

### 3a CBC mode of 16 bytes

Buy and sell actions have 1 block only whereas sell everything and hold and see have 2 blocks. Number of blocks reveal the user potential action

### 3b CTR mode

Since IV resets to 16 bits of 0 after every restart, then attackers can retrieve the very first time the phone boots up and retrieve all the plain text

## Question 4 Padding Oracle

### Analysis

Attacker knows the plain text must end in 00 00 ff 04 04 04 04, it most likely follows PKCS#7 convention.

Force out 08 8 times by editing the last 7 bytes to 08 in the plain text. Since $P_1 = D_k (C_1) \oplus IV$, the offset needed to convert those to 08 is also the offset needed for the forged IV.

```python
IV = [t, v1, v2, v3, v4, v5, v6, v7]
for t in range(0xff):
    payload = ''.join(IV)
    # send payload to server
    if server accpts:
        print(payload)   
```

## Question 5 Padding Oracle

To find the padding of plaintext, do a binary search by flipping bytes

Server rejects implies the byte that has been flipped is in the padding region, decrement the index

Server accepts implies the byte that has been flipped is not in the padding region, increase the index

Repeat until it converges to a value.
