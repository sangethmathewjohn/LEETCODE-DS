# LeetCode DS

## DAY 1

### Contain Duplicate

#### By creating a set:

    class Solution:
        def containsDuplicate(self, nums: List[int]) -> bool:
            sets=[]
            for i in nums:
                if i in sets:
                    return True
                sets.append(i)
            return False
            
#### By Sorting
    
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
        
### Maximum Subarray

#### Bruteforcing(normal)

        class Solution:
            def maxSubArray(self, nums: List[int]) -> int:
                maxi=min(nums)-1
                new=[]
                if len(nums)<=1:
                    return nums[0]
                for i in range(len(nums)):
                    for j in range(i,len(nums)):
                        if sum(nums[i:j+1])>maxi:
                            maxi=sum(nums[i:j+1])
                            new=sum(nums[i:j+1])
                return new
