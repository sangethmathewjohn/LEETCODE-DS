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
            
### By Sorting
    
    class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        
        nums.sort()
        l=len(nums)
        if l==1:
            return False
        for i in range(l):
            if nums[i]==nums[i-1]:
                return True
        return False
