# Finding-Duplicate-LeetCode

### By creating a set:

    class Solution:
        def containsDuplicate(self, nums: List[int]) -> bool:
            sets=[]
            for i in nums:
                if i in sets:
                    return True
                sets.append(i)
            return False
