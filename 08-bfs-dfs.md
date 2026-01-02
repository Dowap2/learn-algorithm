# 08-bfs-dfs.md

## BFS / DFS

### DFS

- 경로 탐색
- 백트래킹
- 재귀 / 스택

### BFS

- 최단 거리 (가중치 동일)
- 레벨 탐색

### BFS 격자 템플릿

```js
function bfs(grid, sr, sc) {
  const R = grid.length;
  const C = grid[0].length;
  const visited = Array.from({ length: R }, () => Array(C).fill(false));
  const q = [];
  let head = 0;

  q.push([sr, sc]);
  visited[sr][sc] = true;

  const dr = [1, -1, 0, 0];
  const dc = [0, 0, 1, -1];

  while (head < q.length) {
    const [r, c] = q[head++];
    for (let i = 0; i < 4; i++) {
      const nr = r + dr[i];
      const nc = c + dc[i];
      if (nr < 0 || nr >= R || nc < 0 || nc >= C) continue;
      if (visited[nr][nc]) continue;
      visited[nr][nc] = true;
      q.push([nr, nc]);
    }
  }
}
```
