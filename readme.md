 # 🚀 Must-Do Coding Interview Questions

## 📌 Table of Contents
- [Arrays](#arrays)
- [Strings](#strings)
- [Linked List](#linked-list)
- [Stack & Queue](#stack--queue)
- [Trees](#trees)
- [Graphs](#graphs)
- [Dynamic Programming](#dynamic-programming)
- [Sliding Window](#sliding-window)
- [Binary Search](#binary-search)
- [Backtracking](#backtracking)
- [Heap](#heap)
- [Two Pointers](#two-pointers)

## Arrays

1  Minimum Size Subarray Sum | leetode 209 | [solution](#Q1)

# Solution

## Q1

```
int minSubArrayLen(int target, vector<int>& nums) {
    int left = 0, right = 0;
    int sum = 0;
    int minLen = INT_MAX;
    int n = nums.size();

    while (right < n) {
        sum += nums[right];
        right++;

        while (sum >= target) {          // shrink window from left
            minLen = min(minLen, right - left);
            sum -= nums[left];
            left++;
        }
    }

    return minLen == INT_MAX ? 0 : minLen;
}

int main() {
    cout << "Hello World" << endl;
    return 0;
}
```
