# 05-stack-queue.md

## 스택 / 큐

### 스택 (LIFO)

- 괄호 검사
- 되돌리기
- 단조 스택

### 큐 (FIFO)

- BFS
- 작업 순서 처리

### JS 큐 구현 (포인터 방식)

```js
class Queue {
  constructor() {
    this.arr = [];
    this.head = 0;
  }
  push(x) {
    this.arr.push(x);
  }
  pop() {
    return this.arr[this.head++];
  }
  size() {
    return this.arr.length - this.head;
  }
}
```
