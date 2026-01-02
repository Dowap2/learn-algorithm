# 07-heap.md

## 힙 (우선순위 큐)

### 언제 쓰나

- 최대/최소값 반복 추출
- 작업량 줄이기 문제

### 시간복잡도

- 삽입 / 삭제: O(log n)

### MinHeap 템플릿

```js
class MinHeap {
  constructor() {
    this.heap = [];
  }

  push(x) {
    this.heap.push(x);
    let i = this.heap.length - 1;
    while (i > 0) {
      const p = Math.floor((i - 1) / 2);
      if (this.heap[p] <= this.heap[i]) break;
      [this.heap[p], this.heap[i]] = [this.heap[i], this.heap[p]];
      i = p;
    }
  }

  pop() {
    if (this.heap.length === 1) return this.heap.pop();
    const top = this.heap[0];
    this.heap[0] = this.heap.pop();

    let i = 0;
    while (true) {
      let l = i * 2 + 1,
        r = l + 1,
        s = i;
      if (l < this.heap.length && this.heap[l] < this.heap[s]) s = l;
      if (r < this.heap.length && this.heap[r] < this.heap[s]) s = r;
      if (s === i) break;
      [this.heap[i], this.heap[s]] = [this.heap[s], this.heap[i]];
      i = s;
    }
    return top;
  }
}
```
