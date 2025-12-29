# 02-two-pointers.md

## 투 포인터 (Two Pointers)

### 언제 쓰나

- 정렬된 배열
- 합/차/조건 만족하는 쌍
- 양쪽에서 줄여가며 탐색 가능할 때

### 핵심 아이디어

- left, right 포인터로 탐색 범위를 점점 좁힘
- O(n²)을 O(n)으로 줄일 수 있음

### 자주 실수

- 정렬 안 하고 쓰는 경우
- 조건 만족 시 어느 포인터를 움직일지 헷갈림

### JS 템플릿

```js
function twoPointers(arr, target) {
  arr.sort((a, b) => a - b);
  let l = 0,
    r = arr.length - 1;

  while (l < r) {
    const sum = arr[l] + arr[r];
    if (sum === target) return true;
    if (sum < target) l++;
    else r--;
  }
  return false;
}
```
