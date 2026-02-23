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

## Backtracking

1. Given a collection of candidate numbers (candidates) and a target number (target), find all unique combinations in candidates where the candidate numbers sum to target.

Each number in candidates may only be used once in the combination.

Note: The solution set must not contain duplicate combinations.

Example 1:

Input: candidates = [10,1,2,7,6,1,5], target = 8
Output: 
[
[1,1,6],
[1,2,5],
[1,7],
[2,6]
]

[solution](#Q2)

# 2. Find all valid combinations of k numbers that sum up to n such that the following conditions are true:

Only numbers 1 through 9 are used.
Each number is used at most once.
Return a list of all possible valid combinations. The list must not contain the same combination twice, and the combinations may be returned in any order.

Example 1:

Input: k = 3, n = 7
Output: [[1,2,4]]
Explanation:
1 + 2 + 4 = 7
There are no other valid combinations.
[solution](#Q3)

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


## Q2
```
   void helper(vector<int> &arr,int idx,int target, vector<int> &sumArr, vector<vector<int>> &mem) {
        if ( target == 0) {
            mem.push_back(sumArr);
           return;
        }
        for (int i = idx; i < arr.size(); i++) {
            

            if (target - arr[i] >= 0) {
               sumArr.push_back(arr[i]);
               helper(arr, i+1,target - arr[i], sumArr, mem);
               sumArr.pop_back();
            }
        }
    }
    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        vector<int> sumArr;
        vector<vector<int>> mem;
        sort(candidates.begin(), candidates.end());
        helper(candidates, 0, target, sumArr, mem);
        return mem;
    }
```


## Q3
```
 void helper(int idx, int target,int k, vector<int> &sumArr, int n, vector<vector<int>> &res) {
    if (target == 0 && k == 0) {
        res.push_back(sumArr);
        return;
    }

    if (k == 0 || target == 0) {
        return;
    }

    for (int i = idx; i <= 9; i++) {
        if (target - i >= 0) {
         sumArr.push_back(i);
         helper( i+1, target - i, k-1, sumArr, n, res);
         sumArr.pop_back();
        }
    }
   }
    vector<vector<int>> combinationSum3(int k, int n) {
        vector<vector<int>> comb;
        vector<int> sumArr;
        helper(1, n, k, sumArr, n, comb);
        return comb;
    }
```
