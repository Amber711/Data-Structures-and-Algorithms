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

	for(let i = 0; i < len, i++) {
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
