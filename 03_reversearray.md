
---

# 🔁 Reverse an Array In-Place (C++)

This repository contains a simple yet efficient C++ implementation to **reverse an array in-place**. It uses the classic **Two-Pointer Pattern**, achieving optimal time and space complexity.

---

## ✅ Problem Statement

Given an array of integers, reverse its elements **in-place**, i.e., without using any additional data structures. The first element should become the last, the second should become second-last, and so on.

---

## 💡 Approach: Pattern Technique

This solution applies the **Two-Pointer Pattern**, which is ideal for problems involving symmetrical traversal from both ends of a data structure:

- One pointer (`first`) starts from the beginning.
- The other (`last`) starts from the end.
- Swap values and move both pointers towards the center.

This pattern ensures a clean and fast in-place reversal of the array.

---

## 👨‍💻 Code

```cpp
class Solution {
  public:
    void reverseArray(vector<int> &arr) {
        int first = 0;
        int last = arr.size() - 1;
        if(arr.size() == 1) return;
        int n = arr.size();
        
        while(first < n / 2){
            swap(arr[first], arr[last]);
            first++;
            last--;
        }
    }
};
```

---

## 🧠 Explanation

- If the array has only one element, no reversal is needed.
- Use two pointers: `first` at index `0`, `last` at index `n - 1`.
- In a loop that runs until the midpoint:
  - Swap `arr[first]` and `arr[last]`.
  - Move `first` forward and `last` backward.
- The loop ensures that the array is reversed **in-place**.

---

## 🕒 Complexity

- **Time Complexity**: `O(n / 2)` → effectively `O(n)`
- **Space Complexity**: `O(1)` — constant space

---

## 📌 Edge Cases

- Array of size `1`: no action needed
- Already reversed array: still works correctly
- Palindromic array: remains the same after reversal

---

Let me know if you'd like a visual example section or markdown file export too!