# 10-greedy.md

## 그리디

### 언제 쓰나

- 매 순간 최선의 선택이 전체 최적해일 때
- 증명 가능해야 안전

### 대표 예시

- 동전 거스름돈
- 회의실 배정
- 최소 이동 횟수

### 체크 포인트

- 정렬 기준이 핵심
- 반례 꼭 생각하기

### 예시 (회의실 배정)

```js
function schedule(meetings) {
  meetings.sort((a, b) => a[1] - b[1]);
  let count = 0;
  let end = 0;

  for (const [s, e] of meetings) {
    if (s >= end) {
      count++;
      end = e;
    }
  }
  return count;
}
```
