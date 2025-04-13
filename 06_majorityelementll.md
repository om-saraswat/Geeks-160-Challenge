

# 🗳️ Find Elements Occurring More Than ⌊n/3⌋ Times (C++)

This repository provides an efficient C++ implementation to find **all elements that appear more than ⌊n/3⌋ times** in an array. This is an extension of the **Boyer-Moore Majority Voting Algorithm**, optimized for the case where elements may appear more than n/3 times.

---

## ✅ Problem Statement

Given an integer array `arr` of size `n`, return **all elements** that appear **more than ⌊n/3⌋ times**. The solution must run in linear time and use constant space.

---

## 💡 Pattern Technique: Extended **Boyer-Moore Majority Voting**

### 🔹 Standard Boyer-Moore (for n/2):
Finds the single majority element appearing more than ⌊n/2⌋ times.

### 🔸 Extended Version (for n/3):
At most **two** elements can appear more than ⌊n/3⌋ times. So we:
- Track two potential candidates.
- Use two counters.
- Verify counts after identifying candidates.

This pattern is ideal when a constraint limits the number of possible "majority" elements.

---

## 👨‍💻 Code

```cpp
vector<int> findMajority(vector<int>& arr) {
    int element1, element2;
    int cnt1 = 0, cnt2 = 0;
    int n = arr.size();
    vector<int> v;

    // First pass: find potential candidates
    for(int i = 0; i < n; i++) {
        if(cnt1 == 0 && arr[i] != element2) {
            cnt1++;
            element1 = arr[i];
        }
        else if(cnt2 == 0 && arr[i] != element1) {
            cnt2++;
            element2 = arr[i];
        }
        else if(arr[i] == element1) cnt1++;
        else if(arr[i] == element2) cnt2++;
        else {
            cnt1--;
            cnt2--;
        }
    }

    // Second pass: validate the candidates
    cnt1 = cnt2 = 0;
    for(int i = 0; i < n; i++) {
        if(arr[i] == element1) cnt1++;
        if(arr[i] == element2) cnt2++;
    }

    int need = n / 3 + 1;
    if(cnt1 >= need) v.push_back(element1);
    if(cnt2 >= need && element2 != element1) v.push_back(element2);

    sort(v.begin(), v.end());
    return v;
}
```

---

## 🧠 Step-by-Step Working

Example: `arr = [3, 2, 3, 2, 2, 1, 1]`

- **First Loop**:
  - Picks two potential elements that could be > n/3.
- **Second Loop**:
  - Confirms if they actually appear more than n/3 times.
- **Returns** sorted list of valid candidates.

---

## 🕒 Complexity

| Metric          | Value     |
|-----------------|-----------|
| Time Complexity | O(n)      |
| Space Complexity| O(1)      | *(excluding result vector)*

---

## 📌 Edge Cases

- All elements same → returns that single element.
- No element occurs more than n/3 → returns empty list.
- Multiple valid elements → returns them sorted.
- Array of length 1 or 2 → all elements are majority.

---

## 🔎 Real-World Applications

- Data stream analytics (frequent items)
- Voting systems
- Distributed systems (e.g., consensus)

---

Let me know if you want this in `.md` format for download or a version with visual walkthroughs/examples!