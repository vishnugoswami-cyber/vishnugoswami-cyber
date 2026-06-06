# Attacks and Defenses

---

## The CIA Triad

Protecting digital data has become a core requirement for governments, organisations, and individuals.

In cybersecurity, being secure means ensuring specific conditions for digital data. These conditions are the key aspects around which security revolves:

- **Confidentiality**
- **Integrity**
- **Availability**

These principles are known as the **CIA Triad**.

---

### ✦ Confidentiality

Confidentiality ensures that sensitive data can only be accessed by authorised individuals. If confidentiality is not maintained, unauthorised individuals can access the data, resulting in financial loss, privacy violations, or legal consequences.

> **Confidentiality** – Ensuring digital information is not available to unauthorised individuals.

---

### ✦ Integrity

Integrity ensures that unauthorised individuals do not modify data. Without integrity, data can be altered and no longer be trusted. Unauthorised changes in data can sometimes lead to dangerous consequences.

> **Integrity** – Ensuring digital information is not modified without permission.

---

### ✦ Availability

Availability ensures that data and services are available to authorised users when needed.

> **Availability** – Ensuring digital information is not unavailable when needed.

---

## Cryptography Concepts

How do we actually protect secrets and detect tampering in the real world? That's where cryptography comes in.

Cryptography is a mathematical suite and secret keys to scramble information into gibberish that only authorised people can unscramble.

---

## Hiding Information – Symmetric Encryption

### Understanding the Basics

- **Plaintext** – A message you can read normally, like `HELLO` or `RECORD`.

- **Ciphertext** – A scrambled version that is not supposed to make sense, like `KHOOR` or `Vplwt`.

- **Key** – The secret ingredient that controls how scrambling and unscrambling work. Think of it as a password that the algorithm uses.

- **Algorithm** – The public recipe — the set of steps that explain how to use the key on the message.

---

### Encryption & Decryption Process

```
Encryption:
Plaintext + Encryption Algorithm + Key ──→ Ciphertext

Decryption:
Ciphertext + Decryption Algorithm + Key ──→ Plaintext
```

---

### Plaintext versus Ciphertext

Now, `HELLO` — that is the plaintext — readable message. Alice uses an algorithm and a secret key to scramble it. After scrambling, it becomes `KHOOR`. That is the ciphertext. To anyone without the key, `KHOOR` is meaningless. The key point — ciphertext should look like random nonsense to anyone who doesn't have the key.

---

## The Caesar Cipher – Algorithm Plus Key

To make this concrete, we'll use something called the **Caesar Cipher**.

The Caesar cipher is named after Julius Caesar, who reportedly used this technique over 2000 years ago to send military messages.

### How It Works

The Caesar cipher shifts each letter in your message by a fixed number of positions in the alphabet. That fixed number is your key.

**Let's say the key is 3:**

- `A` shifts forward 3 spots to become `D`
- `B` becomes `E`
- `C` becomes `F` and so on.

If anyone wants to encrypt `HELLO` with a key of `3`:

| Original | Encrypted |
|---|---|
| H | → K |
| E | → H |
| L | → O |
| L | → O |
| O | → R |

So **HELLO** becomes **KHOOR**.

> The Caesar Cipher is not secure and is never used in real systems. It's way too easy to compromise and decrypt messages.
>
> Real algorithms like **AES (Advanced Encryption Standard)** are vastly more complex and secure.

---

## Symmetric Encryption Explained

The Caesar cipher is an example of **symmetric encryption**. This means that:

- The **same key** encrypts (locks) and decrypts (unlocks) the message.
- Both sender and receiver need a copy of that key.
- The key has to stay secret from everyone else.

### Benefits
- It's fast
- It's efficient

---

## Asymmetric Encryption

### Two Keys Instead of One

Asymmetric encryption uses two mathematically linked keys:

- A **public key** that anyone can know and use.
- A **private key** that only one person keeps secret.

**How it works:**
- If you encrypt something with someone's **public key**, only their **private key** can decrypt it.
- If you encrypt something with your **private key**, anyone with your **public key** can decrypt it.

### Real-World Use – HTTPS

The most common everyday use of asymmetric encryption is in **HTTPS** — the secure protocol you use whenever you see that padlock in your browser.

---

*Notes compiled from: Attacks and Defenses — CIA Triad & Cryptography Concepts.*
