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
        
#### Dynamic Programming
                
                class Solution:
                    def maxSubArray(self, nums: List[int]) -> int:
                        n = len(nums)
                        maxi = maxsum = nums[0]
                        for i in range(1, n):
                            maxi = max(maxi + nums[i], nums[i])
                            maxsum = max(maxi, maxsum)

                        return maxsum
## DAY 2

### Two Sum

#### Normal 

    class Solution:
        def twoSum(self, nums: List[int], target: int) -> List[int]:
            new=[]
            n=len(nums)-1
            for i in range(n):
                for j in range(n,-1,-1):
                    if(nums[i]+nums[j]==target):
                        if not i==j:
                            new.append(i)
                            new.append(j)
                            return(new)

#### Using Set

    class Solution:
        def twoSum(self, nums: List[int], target: int) -> List[int]:
            new=[]
            for i in nums:
                sets =nums.copy()
                sets.pop(sets.index(i))
                if (target-i) in sets:
                    new.append(nums.index(i))
                    new.append(sets.index(target-i)+1)
                    return new

### Merge Sorted Array

#### Normal

    class Solution:
        def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
            for i in range(n):
                nums1[m+i] =nums2[i]
            nums1.sort()

### Intersection-of-two-arrays-ii

        class Solution:
            def intersect(self, nums1: List[int], nums2: List[int]) -> List[int]:
                if len(nums1)>len(nums2):
                    n=nums1
                    m=nums2
                else:
                    n=nums2
                    m=nums1
                new=[]
                for i in range(len(m)):
                    if m[i] in n:
                        new.append(m[i])
                        n.remove(m[i])
                return new 
