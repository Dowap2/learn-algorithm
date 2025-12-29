# 03-sliding-window.md

## 슬라이딩 윈도우

### 언제 쓰나

- 연속된 부분 배열
- 최대/최소/조건 만족 길이

### 유형

1. 고정 길이 윈도우
2. 가변 길이 윈도우

### 핵심 포인트

- 오른쪽 포인터로 확장
- 조건 깨지면 왼쪽 포인터 이동

### JS 템플릿

```js
function minLength(arr, S) {
  let sum = 0;
  let left = 0;
  let answer = Infinity;

  for (let right = 0; right < arr.length; right++) {
    sum += arr[right];
    while (sum >= S) {
      answer = Math.min(answer, right - left + 1);
      sum -= arr[left++];
    }
  }
  return answer === Infinity ? 0 : answer;
}
```
