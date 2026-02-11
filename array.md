### 1. Concatenation of Array

##### Given an integer array nums of length n, you want to create an array ans of length 2n where ans[i] == nums[i] and ans[i + n] == nums[i] for 0 <= i < n (0-indexed).

##### Specifically, ans is the concatenation of two nums arrays.

##### Return the array ans.


'''cpp

    class Solution {
    public:
        vector<int> getConcatenation(vector<int>& nums) {
            int n=nums.size();
            vector<int>ans(2*n);

        for(int i=0;i<n;i++){
            ans[i]=nums[i];
            ans[i+n]=nums[i];
        }
            return ans;
        }
    };


### 2. Contains Duplicate

#### Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.

### Code:
'''cpp

    class Solution {
    public:
        bool containsDuplicate(vector<int>& nums) {
            unordered_set<int>store;
            for(int i=0;i<nums.size();i++){
                if(store.count(nums[i]))
                    return true;
                store.insert(nums[i]);
            }
            return false;
        }
    };