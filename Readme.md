Q1.
```javascript

function threeSumClosest(nums, target) {
  nums.sort((a, b) => a - b);
  const n = nums.length;
  let closestSum = Infinity;

  for (let i = 0; i < n - 2; i++) {
    if (i > 0 && nums[i] === nums[i - 1]) {
      continue;
    }

    let left = i + 1;
    let right = n - 1;

    while (left < right) {
      const currentSum = nums[i] + nums[left] + nums[right];

      if (Math.abs(currentSum - target) < Math.abs(closestSum - target)) {
        closestSum = currentSum;
      }

      if (currentSum < target) {
        left++;
      } else if (currentSum > target) {
        right--;
      } else {
        return target;
      }
    }
  }

  return closestSum;
}

const nums = [-1, 2, 1, -4];
const target = 1;
const result = threeSumClosest(nums, target);
console.log(result);
```

Q2.
```javascript
function fourSum(nums, target) {
  const n = nums.length;
  const result = [];

  nums.sort((a, b) => a - b); // Step 1: Sort the array

  for (let i = 0; i < n - 3; i++) {
    if (i > 0 && nums[i] === nums[i - 1]) {
      continue;
    }

    for (let j = i + 1; j < n - 2; j++) {
      if (j > i + 1 && nums[j] === nums[j - 1]) {
        continue;
      }

      let left = j + 1;
      let right = n - 1;

      while (left < right) {
        const sum = nums[i] + nums[j] + nums[left] + nums[right];

        if (sum === target) {
          result.push([nums[i], nums[j], nums[left], nums[right]]);
          left++;
          right--;

          while (left < right && nums[left] === nums[left - 1]) {
            left++;
          }

          while (left < right && nums[right] === nums[right + 1]) {
            right--;
          }
        } else if (sum < target) {
          left++;
        } else {
          right--;
        }
      }
    }
  }

  return result;
}

// Example usage:
const nums = [1, 0, -1, 0, -2, 2];
const target = 0;
console.log(fourSum(nums, target));
// Output: [[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]
```

Q3.
```javascript
function nextPermutation(nums) {
  const n = nums.length;
  let i = n - 2;

  // Step 1: Find the first pair `nums[i]` and `nums[i-1]` such that `nums[i] > nums[i-1]`
  while (i >= 0 && nums[i] >= nums[i + 1]) {
    i--;
  }

  if (i >= 0) {
    let j = n - 1;
    // Step 2: Find the smallest element `nums[j]` such that `nums[j] > nums[i-1]`
    while (j >= 0 && nums[j] <= nums[i]) {
      j--;
    }
    // Step 3: Swap `nums[i-1]` with `nums[j]`
    swap(nums, i, j);
  }

  // Step 4: Reverse the subarray starting from index `i` onwards
  reverse(nums, i + 1);

  return nums;
}

function swap(nums, i, j) {
  const temp = nums[i];
  nums[i] = nums[j];
  nums[j] = temp;
}

function reverse(nums, start) {
  let i = start;
  let j = nums.length - 1;
  while (i < j) {
    swap(nums, i, j);
    i++;
    j--;
  }
}

const nums = [1, 2, 3];
console.log(nextPermutation(nums)); // Output: [1, 3, 2]
```

Q4.
```javascript
function searchInsert(nums, target) {
  let left = 0;
  let right = nums.length - 1;
  let mid =0;

  while (left <= right) {
    mid = Math.floor((left + right) / 2);

    if (target === nums[mid]) {
      return `target found at index ${mid}`;
    } else if (target > nums[mid]) {
      left = mid + 1;
    } else if(target < nums[mid]){
      right = mid - 1;
    }
  }
  return `Target is not found and thus target should be inserted at index ${left}`;
}

const nums = [1, 3, 5, 6];
const target = 5;
console.log(searchInsert(nums, target));

```
Q5.
```javascript
function increment(digits) {
	if (digits[digits.length - 1] < 9) {
		digits[digits.length - 1] = digits[digits.length - 1] + 1;
		return digits;
	}
	let str = "";
	for (const digit of digits) {
		str = str + String(digit);
	}
	let num = Number(str);
	num = num + 1;
	str = String(num);
	for (let index = 0; index < str.length; index++) {
		digits[index] = Number(str[index]);
	}
	return digits;
}
console.log(increment([4, 6, 7]));
```


Q6.
```javascript
  function find(nums) {
	let uniqueNum = 0;
	for (const num of nums) {
		uniqueNum = uniqueNum ^ num;
	}
	return uniqueNum;
}
```

Q7.
```javascript
function listOfRanges(lower, upper, nums) {
	let lowerRange = 0;
	let upperRange = 0;
	let range = [];
	const n = nums.length;
	for (let i = 0; i < n; i++) {
		if (i === 0 && nums[i] - lower !== 0) {
			lowerRange = lower;
			upperRange = nums[i] - 1;
			range.push([lowerRange, upperRange]);
		}
		if (i === n - 1 && upper - nums[i] !== 0) {
			lowerRange = nums[i] + 1;
			upperRange = upper;
			range.push([lowerRange, upperRange]);
		}
		if (1 <= i && i < n - 1 && nums[i + 1] - nums[i] !== 0) {
			lowerRange = nums[i] + 1;
			upperRange = nums[i + 1] - 1;
			range.push([lowerRange, upperRange]);
		}
	}
	return range;
}
```

Q8.
```javascript
   function checkMeetings(intervals) {
	intervals.sort((a, b) => a[0] - b[0]);
	const n = intervals.length;
	for (let i = 0; i < n - 1; i++) {
		if (intervals[i][1] > intervals[i + 1][0]) {
			return false;
		}
	}
	return true;
}
```