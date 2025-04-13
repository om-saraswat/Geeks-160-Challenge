

# 🔍 Find Second Largest Element in Array (C++)

This repository contains a simple and efficient solution to find the **second largest element** in an array using **C++**. The approach uses the **Pattern Technique**, which focuses on identifying a template or structure to solve similar types of problems efficiently.

---

## ✅ Problem Statement

Given an array of integers, the task is to find the **second largest element** in the array. If no such element exists (e.g., all elements are the same), return `-1`.

---

## 💡 Approach: Pattern Technique

This solution follows the **Single Pass Pattern**, where we:

1. Maintain two variables:
   - `largest` (to store the largest element found so far)
   - `slargest` (to store the second largest)
2. Iterate through the array only **once**.
3. Update the variables according to the comparison conditions.

This pattern avoids sorting and reduces time complexity to **O(n)** with **O(1)** space.

---

## 👨‍💻 Code

```cpp
// User function template for C++
class Solution {
  public:
    // Function returns the second
    // largest elements
    int getSecondLargest(vector<int> &arr) {
        int slargest = INT_MIN;
        int largest = INT_MIN ;

        for(int i = 0; i < arr.size(); i++) {
            if(arr[i] > largest) {
                slargest = largest;
                largest = arr[i];
            }
            else if(arr[i] > slargest && arr[i] != largest) {
                slargest = arr[i];
            }
        }

        return (slargest == INT_MIN) ? -1 : slargest;
    }
};
```

---

## 🧠 Explanation

- Initialize `largest` and `slargest` to `INT_MIN` (smallest integer).
- Loop through each element:
  - If the element is greater than `largest`, update `slargest` to `largest` and `largest` to the current element.
  - Else if it's greater than `slargest` and not equal to `largest`, update `slargest`.
- After the loop, if `slargest` is still `INT_MIN`, it means there was no valid second largest value.

---

## 🕒 Complexity

- **Time Complexity**: `O(n)`
- **Space Complexity**: `O(1)`

---

## 📌 Edge Cases

- All elements equal: return `-1`
- Array with a single element: return `-1`
- Second largest exists only once: still works perfectly

---

Let me know if you'd like this formatted as an actual file or want other languages/approaches too!