# LEETCODE-Strings-1930
**full dry run**

```
s = "aabca"
```

Goal: Count **unique palindromic subsequences of length 3**, of the form **ch + mid + ch**.

---

# ✅ Step-by-Step Dry Run

## **String:** `"aabca"`

Index positions:

```
0 1 2 3 4
a a b c a
```

---

# **STEP 1 — Build `hash` set of unique characters in `s`**

Loop: for(char ch : s.toCharArray())

Characters encountered: a, a, b, c, a

So:

```
hash = { 'a', 'b', 'c' }
```

---

# **STEP 2 — Process each character in `hash`**

We process in some order (HashSet is unordered, but assume: a, b, c)

---

# ⭐ PROCESSING CHARACTER `'a'`

### Find first and last occurrence of `'a'`:

Scan the string:

| i | s[i] | first     | last     |
| - | ---- | --------- | -------- |
| 0 | a    | first = 0 | last = 0 |
| 1 | a    | last = 1  |          |
| 2 | b    | -         | -        |
| 3 | c    | -         | -        |
| 4 | a    | last = 4  |          |

So:

```
first = 0
last = 4
```

### Middle characters from index 1 to 3 (exclusive):

Indices: 1, 2, 3
Characters:

```
a, b, c
```

Set formed:

```
set = { 'a', 'b', 'c' }
```

Add to result:

```
result += 3
result = 3
```

So palindromes are:

* a a a
* a b a
* a c a

---

# ⭐ PROCESSING CHARACTER `'b'`

### Find first + last occurrence of 'b':

| i | s[i] | first     | last     |
| - | ---- | --------- | -------- |
| 0 | a    | -         | -        |
| 1 | a    | -         | -        |
| 2 | b    | first = 2 | last = 2 |
| 3 | c    | -         | -        |
| 4 | a    | -         | -        |

So:

```
first = 2
last = 2
```

### Now third loop:

Middle range = first+1 to last-1 = **3 to 1** → invalid range.

→ No middle characters
→ set = { }

So:

```
result += 0
result = 3
```

---

# ⭐ PROCESSING CHARACTER `'c'`

### Find first + last occurrence of 'c':

| i | s[i] | first     | last     |
| - | ---- | --------- | -------- |
| 0 | a    | -         | -        |
| 1 | a    | -         | -        |
| 2 | b    | -         | -        |
| 3 | c    | first = 3 | last = 3 |
| 4 | a    | -         | -        |

So:

```
first = 3
last = 3
```

Middle range = 4 to 2 → invalid
No characters

So:

```
result += 0
result = 3
```

---

# 🎉 FINAL RESULT

```
result = 3
```

---

# **ANSWER**

### ✔ Output for input `"aabca"` is:

```
3
```

---
