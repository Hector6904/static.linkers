# The Misplaced Finger

**CTF:** [CTF Name]
**Category:** Cryptography
**Difficulty:** Easy

---

## Challenge Description

> A typist has shifted their entire hand 1 row DOWN and 1 key to the LEFT on a standard QWERTY keyboard. Every character in the flag was typed while their hands were in this offset position.
>
> **Ciphertext:** `X_K_O_D_X_Z_R_Y_B_Z_D_S`
>
> **Hint:** If they intended to type 'Q', their finger landed elsewhere. Map the keys back!
>
> **Flag Format:** `CIPH{TEXT}`

---

## Understanding the Cipher

The typist's hand is shifted **1 row down** and **1 key to the left**. So when they *intend* to press a key, their finger actually lands on the key that is 1 row down and 1 to the left of the intended key.

To decode, we reverse this — for each ciphertext character, we find the key that is **1 row up and 1 to the right**.

Standard QWERTY layout (relevant rows):

```
Row 1:  Q W E R T Y U I O P
Row 2:  A S D F G H J K L
Row 3:  Z X C V B N M
```

---

## Solving

Mapping each ciphertext character → intended character (1 up, 1 right):

| Ciphertext | Intended |
|------------|----------|
| X          | D        |
| K          | O        |
| O          | 0 (zero) |
| D          | R        |
| X          | D        |
| Z          | S        |
| R          | 5        |
| Y          | 7        |
| B          | H        |
| Z          | S        |
| D          | R        |
| S          | E        |

**Decoded string:** `DO0RDS57HSRE`

> **Note:** Keys like `O` and `Y` sit in the top letter row, so shifting them "up" takes you into the **number row** — `O` maps to `0` and `Y` maps to `7`, based on their physical positions on a QWERTY keyboard.

---

## Flag

```
CIPH{DO0RDS57HSRE}
```

---

## Key Takeaway

The tricky part was handling keys in the **top letter row (Q–P)** — shifting them "up" takes you into the **number row**, not back to another letter row. Once that mapping was applied consistently, the decode fell into place.
