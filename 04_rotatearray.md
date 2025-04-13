
---

# 🔄 Rotate Array to the Left by `d` Positions (C++)

This repository provides an efficient solution to **rotate an array to the left by `d` positions**. It demonstrates both a **brute force** and an **optimized** approach using the **Reversal Algorithm**, which is based on the **Three-Step Reversal Pattern**.

---

## ✅ Problem Statement

Given an array and a number `d`, rotate the array to the left by `d` positions. The rotation should be done **in-place**, without using extra space.

---

## 🐢 Brute Force Approach

### 🔸 Idea:

- Create a temporary array.
- Copy elements from index `d` to end, then from index `0` to `d-1`.
- Copy this back to original array.

### 🔹 Time & Space:

- **Time Complexity**: `O(n)`
- **Space Complexity**: `O(n)` (extra array used)

### 🔧 Code (Brute Force):

```cpp
void rotateArr(vector<int>& arr, int d) {
    int n = arr.size();
    vector<int> temp(n);
    for(int i = 0; i < n; i++) {
        temp[i] = arr[(i + d) % n];
    }
    arr = temp;
}
```

---

## 🚀 Optimized Approach: Reversal Algorithm

### 💡 Pattern Technique: **Three-Step Reversal**

This is an in-place rotation using a pattern of **three reversals**:

1. **Reverse the first `d` elements**
2. **Reverse the remaining `n-d` elements**
3. **Reverse the entire array**

This results in the desired rotation with **O(1)** extra space.

---

## 👨‍💻 Code (Optimized)

```cpp
void rotateArr(vector<int>& arr, int d) {
    d = d % arr.size();  // Handle d > n
    reverse(arr.begin(), arr.begin() + d);        // Step 1
    reverse(arr.begin() + d, arr.end());          // Step 2
    reverse(arr.begin(), arr.end());              // Step 3
}
```

---

## 🧠 Explanation

For example, rotating `[1, 2, 3, 4, 5, 6, 7]` by `d = 2`:

1. Reverse first 2 → `[2, 1, 3, 4, 5, 6, 7]`
2. Reverse rest     → `[2, 1, 7, 6, 5, 4, 3]`
3. Reverse all      → `[3, 4, 5, 6, 7, 1, 2]`

Final result = Left-rotated array by 2.

---

## 🕒 Complexity

| Approach       | Time     | Space    |
|----------------|----------|----------|
| Brute Force    | O(n)     | O(n)     |
| Reversal Algo  | O(n)     | O(1)     |

---

## 📌 Edge Cases

- `d = 0`: No rotation
- `d > n`: Use `d % n` to normalize
- Array size = 1: No change
- All elements same: Still valid

---

Let me know if you'd like a downloadable `.md` file, illustrations, or to expand this to **right rotation** as well!