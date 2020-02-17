# minshu\

把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个递增排序的数组的一个旋转，输出旋转数组的最小元素。例如，数组 [3,4,5,1,2] 为 [1,2,3,4,5] 的一个旋转，该数组的最小值为1。  

示例 1：

输入：[3,4,5,1,2]
输出：1

示例 2：

输入：[2,2,2,0,1]
输出：0

class Solution:
    def minArray(self, numbers: List[int]) -> int:

        if numbers[0] < numbers[-1]:
            return numbers[0]
        if len(numbers) < 3: 
            return min(numbers)

        mid = len(numbers)>>1
        if numbers[mid] > numbers[0]:
            return self.minArray(numbers[mid+1:])
        if numbers[mid] < numbers[-1]:
            return self.minArray(numbers[:mid+1])
        return min(self.minArray(numbers[mid+1:]), self.minArray(numbers[:mid+1]))

