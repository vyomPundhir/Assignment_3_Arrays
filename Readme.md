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