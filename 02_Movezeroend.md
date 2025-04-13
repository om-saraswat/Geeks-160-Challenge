
---

# 🚚 Push All Zeros to End of Array (C++)

This repository contains an optimized C++ solution to move all `0`s in a given array to the end **without changing the order of non-zero elements**. The solution utilizes the **Two-Pointer Pattern**, ensuring **in-place transformation** with **O(n)** time complexity.

---

## ✅ Problem Statement

Given an array of integers, move all the `0`s to the end of the array while maintaining the relative order of non-zero elements. The operation should be done **in-place**, without using extra space.

---

## 💡 Approach: Pattern Technique

This solution applies the **Two-Pointer Pattern**, where two indices (`first` and `second`) are used to track positions within the array:

- `first`: Tracks the position of a zero that could potentially be swapped.
- `second`: Moves ahead to find the next non-zero element to swap with.

This pattern is highly effective for problems that involve **in-place reordering**.

---

## 👨‍💻 Code

```cpp
class Solution {
  public:
    void pushZerosToEnd(vector<int>& arr) {
        int first = 0;
        int second = 1;
        int n = arr.size();
        
        while(second < n){
            if(arr[first] == 0 && arr[second] != 0){
                swap(arr[first], arr[second]);
                first++;
            }   
            
            if(arr[first] != 0){
                first++;
            }
            second++;
        }
    }
};
```

---

## 🧠 Explanation

- Initialize two pointers: `first = 0`, `second = 1`.
- Traverse while `second < arr.size()`:
  - If `arr[first]` is `0` and `arr[second]` is not `0`, swap them and move `first`.
  - If `arr[first]` is not `0`, move `first` ahead.
  - Always move `second` forward.
- The algorithm ensures non-zero elements remain in original order, and `0`s are pushed to the end.

---

## 🕒 Complexity

- **Time Complexity**: `O(n)` — Each element is visited once.
- **Space Complexity**: `O(1)` — No extra space used.

---

## 📌 Edge Cases

- All elements are zero: array remains the same.
- No zero present: array remains unchanged.
- Zeros already at end: no extra swaps done.
- Single-element array: unchanged.

---

Let me know if you'd like a Python version of this, or an actual downloadable `.md` file!