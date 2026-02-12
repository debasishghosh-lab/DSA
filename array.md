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

### 3. Valid Anagram

#### Given two strings s and t, return true if t is an anagram of s, and false otherwise.

### code:

'''cpp

        class Solution {
    public:
        bool isAnagram(string s, string t) {
        if(s.length()!=t.length())
                return false;

        int freq[26]={0};

            for(int i=0;i<s.length();i++){
                freq[s[i]-'a']++;
                freq[t[i]-'a']--;
            }
            for(int i=0;i<26;i++){
                if(freq[i])
                    return false;
            }
            return true;
        }
    };

### 4.Two Sum

#### Given an array of integers nums and an integer target, return the indices i and j such that nums[i] + nums[j] == target and i != j.

#### You may assume that every input has exactly one pair of indices i and j that satisfy the condition.

#### Return the answer with the smaller index first.

### code:

'''cpp

    class Solution {
            public:
                vector<int> twoSum(vector<int>& nums, int target) {
                    unordered_map<int,int>hash;

                    for(int i=0;i<nums.size();i++){
                        int rem=target-nums[i];

                        if(hash.find(rem)!=hash.end())
                            return {hash[rem],i};
                        
                        hash[nums[i]]=i;
                    }
                }
        };


### 5.Longest Common Prefix

#### Write a function to find the longest common prefix string amongst an array of strings.

#### If there is no common prefix, return an empty string "".

#### Example:
    - Input: strs = ["flower","flow","flight"]
    - Output: "fl"

#### code:

#### approach 1:

'''cpp

    class Solution {
    public:
        string longestCommonPrefix(vector<string>& strs) {
            string first=strs[0];
            string final_ans=strs[0];
            for(auto it:strs){
                string ans="";
                string ele=it;
                int len = min(final_ans.length(), it.length());
                for(int i=0;i<len;i++){
                    if(final_ans[i]==it[i]){
                        ans+=it[i];
                    }else{
                        
                        break;
                    }
                }
                final_ans=ans;
            }
            return final_ans;
        }
    };

#### approach 2:

'''cpp

    class Solution {
    public:
        string longestCommonPrefix(vector<string>& strs) {
        sort(strs.begin(),strs.end());

        string first_element=strs[0];
        string last_element=strs[strs.size()-1];

        
        int length=min(first_element.length(),last_element.length());
        string prefix="";
        for (int i=0;i<length;i++){
                if(first_element[i]==last_element[i]){
                    prefix+=first_element[i];
                }else{
                    break;
                }
        }
        return prefix;
        }
    };