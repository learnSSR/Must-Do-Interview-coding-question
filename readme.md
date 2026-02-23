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
/*
 Given an array of positive integers nums and a positive integer target, return the minimal length of a subarray whose sum is greater than or equal to target. If there is no such subarray, return 0 instead.

Input: target = 7, nums = [2,3,1,2,4,3]
Output: 2
Explanation: The subarray [4,3] has the minimal length under the problem constraint.
*/
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
