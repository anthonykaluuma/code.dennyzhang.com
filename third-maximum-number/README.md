# Leetcode: Third Maximum Number     :BLOG:Basic:


---

Third Maximum Number  

---

Given a non-empty array of integers, return the third maximum number in this array. If it does not exist, return the maximum number. The time complexity must be in O(n).  

    Example 1:
    Input: [3, 2, 1]
    
    Output: 1
    
    Explanation: The third maximum is 1.

    Example 2:
    Input: [1, 2]
    
    Output: 2
    
    Explanation: The third maximum does not exist, so the maximum (2) is returned instead.

    Example 3:
    Input: [2, 2, 3, 1]
    
    Output: 1
    
    Explanation: Note that the third maximum here means the third maximum distinct number.
    Both numbers with value 2 are both considered as second maximum.

Github: [challenges-leetcode-interesting](https://github.com/DennyZhang/challenges-leetcode-interesting/tree/master/third-maximum-number)  

Credits To: [Leetcode.com](https://leetcode.com/problems/third-maximum-number/description/)  

Leave me comments, if you know how to solve.  

    class Solution(object):
        def thirdMax(self, nums):
            """
            :type nums: List[int]
            :rtype: int
            """
            count = 3
            max_list = [None] * count
            for num in nums:
                # Find where to insert
                insert_index = -1
                for i in range(0, count):
                    max_value = max_list[i]
                    if max_value is None:
                        insert_index = i
                        break
                    elif num == max_value:
                        insert_index = -1
                        break
                    elif num > max_value:
                        insert_index = i
                        break
    
                # insert the value
                if insert_index != -1:
                    for i in range(count-1, insert_index, -1):
                        max_list[i] = max_list[i-1]
                    max_list[insert_index] = num
    
            ret = None
            # get status
            if max_list[2] is not None:
                ret = max_list[2]
            else:
                ret = max_list[0]
            # print ret
            return ret
    
    s = Solution()
    s.thirdMax([1, 3])
    s.thirdMax([1, 2])
    s.thirdMax([3, 2, 1])
    s.thirdMax([2, 2, 3, 1])