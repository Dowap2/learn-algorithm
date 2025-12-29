# 06-binary-search.md

## 이진 탐색

### 언제 쓰나

- 정렬된 배열
- 정답이 단조 증가/감소할 때

### lower_bound 템플릿

```js
function lowerBound(arr, target) {
  let l = 0,
    r = arr.length;
  while (l < r) {
    const mid = Math.floor((l + r) / 2);
    if (arr[mid] >= target) r = mid;
    else l = mid + 1;
  }
  return l;
}
```
