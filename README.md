# codellama-leetcode
Codellama solves leetcode

***RESUME: not an intelligence but a search engine***

## 1. Two Sum
https://leetcode.com/problems/two-sum/
### Input
```
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.
```
### Output
```c++
vector<int> twoSum(vector<int>& nums, int target) {
    unordered_map<int, int> map;
    for (int i = 0; i < nums.size(); i++) {
        if (map.find(nums[i]) != map.end()) {
            return {map[nums[i]], i};
        }
        map[target - nums[i]] = i;
    }
    return {};
}
```
## 2. Add Two numbers
https://leetcode.com/problems/add-two-numbers/
### Input
```
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.
```
### Output
```c++
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        // Initialize the result list
        ListNode* result = new ListNode(0);
        ListNode* current = result;

        // Initialize the carry bit
        int carry = 0;

        // Iterate through both lists and add their digits
        while (l1 != nullptr || l2 != nullptr || carry != 0) {
            int sum = carry;
            if (l1 != nullptr) {
                sum += l1->val;
                l1 = l1->next;
            }
            if (l2 != nullptr) {
                sum += l2->val;
                l2 = l2->next;
            }

            // Append the current digit to the result list
            current->next = new ListNode(sum % 10);
            current = current->next;

            // Update the carry bit
            carry = sum / 10;
        }

        return result->next;

    }
```
##  3. Longest Substring Without Repeating Characters
https://leetcode.com/problems/longest-substring-without-repeating-characters
### Input
```
Given a string s, find the length of the longest
substring
without repeating characters.
```

### Output
```c++
int longestSubstring(string s) {
    int maxLength = 0;
    for (int i = 0; i < s.size(); i++) {
        unordered_set<char> seen;
        int currentLength = 0;
        for (int j = i; j < s.size(); j++) {
            if (seen.find(s[j]) != seen.end()) {
                break;
            } else {
                seen.insert(s[j]);
                currentLength++;
            }
        }
        maxLength = max(maxLength, currentLength);
    }
    return maxLength;
}
```
## 4. Median of Two Sorted Arrays
https://leetcode.com/problems/median-of-two-sorted-arrays/
### Input
```
no concat double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2)

```
### Output
```c++
double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
      // Combine the two arrays into a single array
      vector<int> combined = nums1;
      for (int i = 0; i < nums2.size(); ++i) {
          combined.push_back(nums2[i]);
      }

      // Sort the combined array
      sort(combined.begin(), combined.end());

      // If there are an odd number of elements in the combined array, return the middle element
      if (combined.size() % 2 == 1) {
          return combined[combined.size() / 2];
      } else {
          // If there are an even number of elements in the combined array, return the average of the two middle elements
          int mid = combined.size() / 2;
          return (double) (combined[mid - 1] + combined[mid]) / 2;
      }
  }

```
## 5. Longest Palindromic Substring (FAILED)
https://leetcode.com/problems/longest-palindromic-substring/description/

## 6. Zigzag Conversion (FAILED)
https://leetcode.com/problems/zigzag-conversion/

## 7. Reverse Integer
https://leetcode.com/problems/reverse-integer/
### Input
```
https://leetcode.com/problems/reverse-integer/
```
### Output
```c++
int reverse(int x) {
    long result = 0;
    
    while (x != 0) {
        result = result * 10 + x % 10;
        x /= 10;
    }
    
    return (result > INT_MAX || result < INT_MIN) ? 0 : result;
}
```
## 8. String to Integer (atoi) (FAILED)
https://leetcode.com/problems/string-to-integer-atoi/

## 9. Palindrome Number (FAILED)
https://leetcode.com/problems/palindrome-number/

## 10. Regular Expression Matching
https://leetcode.com/problems/regular-expression-matching/
### Input
```
solve c++ https://leetcode.com/problems/regular-expression-matching/
```
### Output
```c++
bool isMatch(const string& s, const string& p) {
    if (p.empty()) return s.empty();
    bool first_match = !s.empty() && (s[0] == p[0] || p[0] == '.');
    if (p[1] == '*') {
        // Recursive case: check if there are other matches after the current one
        return isMatch(s, p.substr(2)) || (first_match && isMatch(s.substr(1), p));
    } else {
        // Base case: check if the current characters match
        return first_match && isMatch(s.substr(1), p.substr(1));
    }
}
```
## 11. Container With Most Water (FAILED)
https://leetcode.com/problems/container-with-most-water/
### Input
```
solve in c++ https://leetcode.com/problems/container-with-most-water/description/
```
## 12. Integer to Roman
https://leetcode.com/problems/integer-to-roman/
### Input
```
solve c++ https://leetcode.com/problems/integer-to-roman/
```
### Output
```c++
class Solution {
public:
    string intToRoman(int num) {
        vector<string> roman = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};
        vector<int> values = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};
        string result;
        
        while (num > 0) {
            for (int i = 0; i < roman.size(); i++) {
                while (num >= values[i]) {
                    num -= values[i];
                    result += roman[i];
                }
            }
        }
        
        return result;
    }
};
```


## Next Permutation
https://leetcode.com/problems/next-permutation/
### Input
```
A permutation of an array of integers is an arrangement of its members into a sequence or linear order.

    For example, for arr = [1,2,3], the following are all the permutations of arr: [1,2,3], [1,3,2], [2, 1, 3], [2, 3, 1], [3,1,2], [3,2,1].

The next permutation of an array of integers is the next lexicographically greater permutation of its integer. More formally, if all the permutations of the array are sorted in one container according to their lexicographical order, then the next permutation of that array is the permutation that follows it in the sorted container. If such arrangement is not possible, the array must be rearranged as the lowest possible order (i.e., sorted in ascending order).

    For example, the next permutation of arr = [1,2,3] is [1,3,2].
    Similarly, the next permutation of arr = [2,3,1] is [3,1,2].
    While the next permutation of arr = [3,2,1] is [1,2,3] because [3,2,1] does not have a lexicographical larger rearrangement.

Given an array of integers nums, find the next permutation of nums.

The replacement must be in place and use only constant extra memory.
```

### Output
```c++
void nextPermutation(vector<int>& nums) {
    int i = nums.size() - 2;
    while (i >= 0 && nums[i + 1] <= nums[i]) {
        i--;
    }
    if (i < 0) {
        sort(nums.begin(), nums.end());
        return;
    }
    int j = nums.size() - 1;
    while (j >= 0 && nums[j] <= nums[i]) {
        j--;
    }
    swap(nums[i], nums[j]);
    reverse(nums.begin() + i + 1, nums.end());
}
```
