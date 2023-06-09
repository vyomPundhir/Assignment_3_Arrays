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
Q4.
```
function searchInsert(nums, target) {
  let left = 0;
  let right = nums.length - 1;

  while (left <= right) {
    const mid = Math.floor((left + right) / 2);

    if (nums[mid] === target) {
      return mid;
    } else if (nums[mid] < target) {
      left = mid + 1;
    } else {
      right = mid - 1;
    }
  }
  return left;
}

const nums = [1, 3, 5, 6];
const target = 5;
console.log(searchInsert(nums, target));

```


Q6.
```javascript
  function singleNumber(nums) {
  let result = 0;
  for (const num of nums) {
    result ^= num;
  }
  return result;
}

const nums = [2, 2, 1];
const result = singleNumber(nums);
console.log(result);

```
Q8.
```javascript
   function canAttendAllMeetings(intervals) {
  intervals.sort((a, b) => a[0] - b[0]); // Sort intervals based on start time

  for (let i = 1; i < intervals.length; i++) {
    if (intervals[i][0] < intervals[i - 1][1]) {
      return false;
    }
  }

  return true;
}

const intervals = [[0, 30], [5, 10], [15, 20]];
console.log(canAttendAllMeetings(intervals));

```