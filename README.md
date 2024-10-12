# codellama-leetcode
Codellama solves leetcode

## Two Sum
https://leetcode.com/problems/two-sum/
### Input
```
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.
```
### Result
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

## Add Two numbers
https://leetcode.com/problems/add-two-numbers/
### Input
```
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.
```
### Result
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

### Result
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
