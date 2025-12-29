# 04-hash-map-set.md

## 해시 (Map / Set)

### 언제 쓰나

- 중복 체크
- 빈도 수 계산
- 빠른 존재 여부 확인

### Map vs Object

- Map: 키 타입 자유, 안전
- Object: 문자열 키만 사용 시

### 빈도 계산 템플릿

```js
function count(arr) {
  const map = new Map();
  for (const x of arr) {
    map.set(x, (map.get(x) ?? 0) + 1);
  }
  return map;
}
```
