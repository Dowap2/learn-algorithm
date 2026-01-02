문제

문제 설명 A도둑과 B도둑이 팀을 이루어 모든 물건을 훔치려고 합니다. 단, 각 도둑이 물건을 훔칠 때 남기는 흔적이 누적되면 경찰에 붙잡히기 때문에, 두 도둑 중 누구도 경찰에 붙잡히지 않도록 흔적을 최소화해야 합니다. 물건을 훔칠 때 조건은 아래와 같습니다. 물건 i를 훔칠 때, A도둑이 훔치면 info[i][0]개의 A에 대한 흔적을 남깁니다. B도둑이 훔치면 info[i][1]개의 B에 대한 흔적을 남깁니다. 각 물건에 대해 A도둑과 B도둑이 남기는 흔적의 개수는 1 이상 3 이하입니다. 경찰에 붙잡히는 조건은 아래와 같습니다. A도둑은 자신이 남긴 흔적의 누적 개수가 n개 이상이면 경찰에 붙잡힙니다. B도둑은 자신이 남긴 흔적의 누적 개수가 m개 이상이면 경찰에 붙잡힙니다. 각 물건을 훔칠 때 생기는 흔적에 대한 정보를 담은 2차원 정수 배열 info, A도둑이 경찰에 붙잡히는 최소 흔적 개수를 나타내는 정수 n, B도둑이 경찰에 붙잡히는 최소 흔적 개수를 나타내는 정수 m이 매개변수로 주어집니다. 두 도둑 모두 경찰에 붙잡히지 않도록 모든 물건을 훔쳤을 때, A도둑이 남긴 흔적의 누적 개수의 최솟값을 return 하도록 solution 함수를 완성해 주세요. 만약 어떠한 방법으로도 두 도둑 모두 경찰에 붙잡히지 않게 할 수 없다면 -1을 return해 주세요.

풀이

첫 시도

```
function solution(info, n, m) {
  let minA = Infinity;

  dp(0, 0, 0);

  function dp(index, a, b) {
    if (a >= minA) return;
    if (b >= m) return;

    if (index === info.length) {
      minA = Math.min(minA, a);
      return;
    }

    dp(index + 1, a + info[index][0], b);
    dp(index + 1, a, b + info[index][1]);
  }

  return minA < n ? minA : -1;
}
```

DFS 방식으로 구현함
결국 모든 방식을 탐색하고 그 중 조건에 맞는 값을 찾는 느낌으로 구현되었음.

이를 DP로 바꾸기 위해 공부
DP의 핵심은 이전에 계산한 값을 다시 계산하지 않는 것
그리고 조건에 맞지 않는 결과는 바로바로 쳐내기

각 하위 문제의 결과 중 가장 효율적인 답을 저장함

```
function solution(info, n, m) {
    const dp = Array.from({length: info.length + 1}, () => {
        return Array(m).fill(Infinity)
    })

    dp[0][0] = 0;

    for(let i = 0; i < info.length; i++){
        const [da, db] = info[i];

        for(let b=0; b< m;b++){
            if(dp[i][b] === Infinity) continue;
            dp[i+1][b] = Math.min(dp[i+1][b], dp[i][b] + da);
            if(b + db < m){
                dp[i+1][b+db] = Math.min(dp[i+1][b+db], dp[i][b]);
            }
        }
    }

    const answer = Math.min(...dp[info.length]);
    return answer < n ? answer : -1;
}
```
