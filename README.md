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
Good. Now we move to:

# Topic 2: Arrays (Python Lists) 
This is one of the most used data structures in interviews.

---

## What is an Array?

An array is a collection of items stored in a single variable.

In Python, we use **lists**.

```python
arr = [10, 20, 30, 40]
```

Each item has an **index** (position).

```
Index:  0   1   2   3
Value: 10  20  30  40
```

---

## How Access Works (O(1))

```python
arr[0]   # 10
arr[2]   # 30
```

This is **O(1)** — instant access.

No searching. No scanning.

---

## Looping Through an Array (O(n))

```python
for x in arr:
    print(x)
```

If array size = n, this runs n times.

That is **O(n)**.

---

## Modifying an Array

### Append (add at end)

```python
arr.append(50)
```

Usually O(1)

---

### Pop (remove last)

```python
arr.pop()
```

O(1)

---

### Insert (slow)

```python
arr.insert(0, 99)
```

This shifts all elements → O(n)

---

## Searching in an Array

### Check if element exists

```python
if 30 in arr:
    print("Found")
```

This is **O(n)** — Python checks one by one.

---

## Why Arrays Can Be Slow

If you need to:

* Search
* Check duplicates
* Count frequencies

Arrays alone are bad.

That’s where **hashmaps** come in.

---

## Common Array Interview Patterns

### 1. Traversing

```python
for i in range(len(arr)):
    print(arr[i])
```

---

### 2. Two Pointer Pattern (later)

Used in sorted arrays.

---

### 3. Sliding Window (later)

Used in subarray problems.

---

## Most Beginner Mistake

People write nested loops without thinking.

Example:

```python
for i in range(len(arr)):
    for j in range(len(arr)):
        if arr[i] == arr[j]:
            print("Duplicate")
```

This is **O(n²)** 💀

We will avoid this.

---

## Important: Index vs Value

### Index-based loop

```python
for i in range(len(arr)):
    print(i, arr[i])
```

---

### Value-based loop

```python
for x in arr:
    print(x)
```

---

## When Arrays Are Not Enough

If problem says:

* “Check if exists”
* “Count frequency”
* “Find duplicates”
* “Find pairs”

→ You probably need a **hashmap**.

---
Alright. Now we hit the **MOST IMPORTANT TOPIC of Day 1**:

# Topic 3: HashMaps (dict & set)

If you master this, **50% of beginner interview problems become easy**.

---

## What is a HashMap?

A HashMap stores data in **key → value** form.

In Python, it’s called a **dictionary (dict)**.

```python
person = {
    "name": "Sai",
    "age": 21
}
```

Here:

* "name" is the key
* "Sai" is the value

---

## Why HashMaps Exist

Imagine this:

You have a list:

```python
arr = [10, 20, 30, 40]
```

To check if 30 exists:

```python
if 30 in arr:   # O(n)
```

Python checks one by one.

---

Now with a dictionary:

```python
d = {10: True, 20: True, 30: True}
```

Check:

```python
if 30 in d:   # O(1)
```

🔥 Instant.

---

## HashMap = Super Fast Memory

HashMaps trade **memory for speed**.

They store data in a way that allows **instant lookup**.

---

## Basic Operations

### Create

```python
d = {}
```

---

### Insert

```python
d["apple"] = 3
```

---

### Access

```python
print(d["apple"])
```

---

### Check existence

```python
if "apple" in d:
    print("Yes")
```

---

### Delete

```python
del d["apple"]
```

---

## What is a Set?

A set is like a dictionary but with only keys.

No values.

```python
s = set()
```

---

### Add

```python
s.add(10)
```

---

### Check

```python
if 10 in s:
    print("Found")
```

---

### Why Sets?

To store **unique values only**.

```python
s = set()
s.add(5)
s.add(5)
s.add(5)

print(s)  # {5}
```

---

## HashMaps in Interviews = Memory

HashMaps let you **remember past elements**.

This is HUGE.

---

## Example: Duplicate Detection

Bad way:

```python
for i in range(len(arr)):
    for j in range(i+1, len(arr)):
        if arr[i] == arr[j]:
            return True
```

⛔ O(n²)

---

Good way:

```python
seen = set()

for x in arr:
    if x in seen:
        return True
    seen.add(x)
```

✅ O(n)

---

## Frequency Counting (Very Important)

Used in:

* Anagram problems
* Character count
* Majority element
* Mode

---

### Example: Count letters

```python
s = "aabbbc"
```

---

### Step-by-step

```python
freq = {}

for ch in s:
    if ch in freq:
        freq[ch] += 1
    else:
        freq[ch] = 1
```

Result:

```python
{'a': 2, 'b': 3, 'c': 1}
```

---

### Python Shortcut

```python
freq[ch] = freq.get(ch, 0) + 1
```

---

## Interview Insight

If the problem says:

* "Count"
* "Frequency"
* "How many times"
* "Duplicate"
* "Exists"

Think: **HASHMAP / SET**

---

## Common Mistake

People do:

```python
if x in arr:
```

Instead of:

```python
if x in seen_set:
```

---

## Time Complexity Summary

| Operation | List | Dict/Set |
| --------- | ---- | -------- |
| Lookup    | O(n) | O(1)     |
| Insert    | O(1) | O(1)     |
| Delete    | O(n) | O(1)     |

---






