# 2 Sum

### Given an array of integers, return indices of the two numbers such that they add up to a specific target.


###### Example:

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

###### Thoughts:
*Creat a mapping object, whose key is the remain value of the current element in the array, and the value of the key is the index of the current element; => check if the current element exists as a key of the mapping object, which means the sum of the current element and the element we looped before is equal to target; the first value of the result will be the index of the current looping element, and the second value of the result will be nums.indexOf(remain)*

```
function twoSum(nums, target) {

	let remainMap = {};  //remainValue : index 
	let result = [];
	let len = nums.length;
	let remain;

	for(let i = 0; i < len; i++) {
		remain = target - nums[i];

		if(remainMap.hasOwnProperty(nums[i])) {
			result[0] = i;
			result[1] = nums.indexOf(remain)
			return result;
		} else {
			remainMap[remain] = i;
		}
	}

	return result;
}
```

###### Complexity:
The time complexity for this solution will be O(n)


### Challenge1: Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2. Please note that your returned answers (both index1 and index2) are not zero-based.

You may assume that each input would have exactly one solution and you may not use the same element twice.

###### Example: Input: numbers={2, 7, 11, 15}, target=9
Output:[1, 2]

###### Thoughts: 

```
function twoSum(numbers, target) {

    let start = 0;
    let end = numbers.length - 1;
    let sum;
    let result = [];
    while (start < end) {
        sum = numbers[start] + numbers[end];
      console.log('start:', start, 'end:', end)
        if(sum > target) {
            end--;
        } else if(sum < target) {
            start++;
        } else if(sum === target) {
           result[0] = start + 1;
           result[1] = end + 1;
            return result
        }
    }
    
    return result;
}
```

```
optimized solution:

var twoSum = function(numbers, target) {
  var l=numbers.length, i=0, j=l-1;
  while (numbers[i]+numbers[j] !== target) {
    numbers[i]+numbers[j] < target ? i++ : j--;
  }
  return [i+1, j+1];
}
```



