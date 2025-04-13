
---

# 🔢 Next Lexicographical Permutation (C++)

This repository provides an efficient C++ implementation to find the **next lexicographical permutation** of a given array of numbers. If such a permutation is not possible (i.e., the array is in descending order), the function rearranges it as the lowest possible (sorted in ascending order).

---

## ✅ Problem Statement

Given an array `arr` of integers representing a permutation, transform the array into the **next permutation** in lexicographical order. Do this **in-place** without allocating extra memory.

---

## 💡 Approach: Pattern Technique

This algorithm uses the **Pivot-Swap-Reverse** pattern:

1. **Find the Pivot** – Rightmost index where `arr[i] < arr[i + 1]`.
2. **Find the Successor** – Rightmost element greater than the pivot.
3. **Swap** the pivot and successor.
4. **Reverse** the suffix starting just after the pivot.

This approach ensures that we move to the *next* possible permutation in dictionary order.

---

## 👨‍💻 Code

```cpp
void nextPermutation(vector<int>& arr) {
    int pivot = -1;
    int n = arr.size();

    // Step 1: Find the pivot
    for(int i = n - 2; i >= 0; i--) {
        if(arr[i] < arr[i + 1]) {
            pivot = i;
            break;
        }
    }

    // Step 2: If no pivot, it's the last permutation
    if(pivot == -1) {
        reverse(arr.begin(), arr.end());
        return;
    }

    // Step 3: Find the next greater element from the end
    for(int i = n - 1; i > pivot; i--) {
        if(arr[i] > arr[pivot]) {
            swap(arr[i], arr[pivot]);
            break;
        }
    }

    // Step 4: Reverse the suffix
    reverse(arr.begin() + pivot + 1, arr.end());
}
```

---

## 🧠 Step-by-Step Working

Example: `arr = [1, 2, 3]`

- Step 1: Pivot is `1` (at index `1`)
- Step 2: Successor is `3` (at index `2`)
- Step 3: Swap → `arr = [1, 3, 2]`
- Step 4: Reverse suffix after pivot → Final: `[1, 3, 2]`

If input is `[3, 2, 1]`, it's the last permutation, so we return the first by reversing it → `[1, 2, 3]`.

---

## 🕒 Complexity

- **Time Complexity**: `O(n)`
- **Space Complexity**: `O(1)`

---

## 📌 Edge Cases

- Already last permutation (descending): Reverse to first
- Already highest unique number at the end
- Single element: No change
- All elements same: No next permutation

---

## 📎 Real-World Usage

- Generating permutations in backtracking or brute-force algorithms
- Lexicographical search or enumeration problems
- Combinatorial optimization

---

Let me know if you’d like a diagram, downloadable markdown, or a version with input/output examples!