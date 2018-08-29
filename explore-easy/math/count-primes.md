## 计数质数
统计所有小于非负整数 n 的质数的数量。

示例:
```
输入: 10
输出: 4
解释: 小于 10 的质数一共有 4 个, 它们是 2, 3, 5, 7 。
```

### 代码

``` js
/**
 * @param {number} n
 * @return {number}
 */
var countPrimes = function(n) {
    let count = 0;
    if(n <= 2) {
        return count;
    }
    for(let i = 2; i < n; i++) {
        if(isPrime(i)) {
            count++;
        }
    }
    return count;
};
function isPrime(num) {
   for (let i = 2; i * i <= num; i++) {
      if (num % i == 0) return false;
   }
   return true;
}
```