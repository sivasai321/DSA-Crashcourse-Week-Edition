# DSA-Crashcourse-Week-Edition
Good. We’ll do this **properly**. No rushing, no fake confidence, no surface-level nonsense. I will make you *actually* interview-ready.

We start with **Topic 1: Big-O Notation** — the foundation of everything.

---

# Topic 1: Big-O 

## What is Big-O?

Big-O is a way to **measure how fast your code grows** when input becomes big.

Not how fast your laptop is.
Not how fast Python is.
But how your *logic* scales.

---

## Why Interviewers Care

They don’t care if your code works for 10 numbers.

They care if your code works for:

* 1,000
* 1,000,000
* 100,000,000

Bad logic = timeouts = rejected.

---

## Real-Life Example

Imagine you’re finding a name in a list of students.

### Way 1: One by one

You check each student:

"Is this John?"
"No"
"Is this John?"
"No"
...

If there are **n** students, you might check **n** times.

This is **O(n)**

---

### Way 2: Phone Contacts

You type the name and it appears instantly.

This is **O(1)** (constant time)

---

## Common Big-O Types You MUST Know

| Big-O    | Meaning       | Example       |
| -------- | ------------- | ------------- |
| O(1)     | Constant time | dict lookup   |
| O(n)     | Linear        | one loop      |
| O(n²)    | Quadratic     | nested loops  |
| O(log n) | Logarithmic   | binary search |

---

## O(1) — Constant Time

Doesn’t depend on input size.

```python
arr = [10, 20, 30]
print(arr[0])
```

Even if the list has 1 million items, this still takes same time.

---

## O(n) — Linear Time

One loop.

```python
for x in arr:
    print(x)
```

If arr has:

* 10 items → 10 operations
* 1,000,000 items → 1,000,000 operations

---

## O(n²) — Very Slow

Nested loops.

```python
for i in arr:
    for j in arr:
        print(i, j)
```

If n = 10 → 100 operations
If n = 1,000 → 1,000,000 operations
If n = 10,000 → 100,000,000 operations 💀

---

## O(log n) — Super Fast

Used in **binary search**.

Each step cuts the data in half.

Example: Guessing number between 1–100

50?
Higher? → 75
Lower? → 62
Lower? → 56

Very few steps.

---

## Interview Rule of Thumb

| Code Type  | Acceptable?    |
| ---------- | -------------- |
| O(1)       | 🔥 Best        |
| O(log n)   | 🔥 Great       |
| O(n)       | ✅ Fine         |
| O(n log n) | ✅ Usually fine |
| O(n²)      | ⚠️ Risky       |
| O(2ⁿ)      | ❌ Terrible     |

---

## How to Recognize Big-O from Code

### 1 Loop → O(n)

```python
for i in arr:
    print(i)
```

---

### 2 Nested Loops → O(n²)

```python
for i in arr:
    for j in arr:
        print(i, j)
```

---

### Loop + Dictionary Lookup → O(n)

```python
for x in arr:
    if x in my_dict:
        print(x)
```

Because:

* Loop = O(n)
* Dict lookup = O(1)

Total = O(n)

---

## Why This Matters for DSA

Most beginner mistakes:

❌ Using nested loops everywhere
❌ Not using hashmaps
❌ Ignoring performance


---


