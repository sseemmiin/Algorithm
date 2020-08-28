# Algorithm for coding test


1. [BOJ_14502_연구소](#1-BOJ_14502_연구소)
2. [BOJ_19235_모노미노도미노](#2-BOJ_19235_모노미노도미노)
3. [SWEA_1285_행렬찾기](#3-SWEA_1825_행렬찾기)
4. [BOJ_17825_주사위 윷놀이](#4-BOJ_17825_주사위-윷놀이)
5. [BOJ_17822_원판돌리기](#5-BOJ_17822_원판돌리기)




---


### 1. [BOJ_14502_연구소](https://www.acmicpc.net/problem/14502)<br>
[코드](./BOJ_연구소.cpp)<br>
시간 : 24ms

BFS와 DFS를 사용하여 안전영역의 최댓값을 구하였다.<br>

1. 최댓값을 구해야 되므로 DFS를 사용해야겠다고 생각했다.<br>
2. 바이러스가 퍼지기 때문에 BFS를 사용해야겠다고 생각했다.<br><br>

사실 이 문제 처음 풀었을 때는 시간이 432ms가 나왔다. (문제의 input size가 더 컸다면 시간초과가 나왔을것이다.)<br>
아래와 같은 방법으로 수정하니 시간을 24ms까지 줄일 수 있었다. <br>
* DFS를 visited 배열을 사용해 이미 체크한 곳은 다시 방문하지 않도록 구현.<br>
 ( 이 부분에서 시간을 가장 많이 줄일 수 있었음) <br>
* DFS도 재귀가 아닌 3중 for문을 사용해 구현할 수 있었다. <br>
* BFS 함수에서 Queue 대신 array 사용 <br><br>

#### 예전에는 문제만 풀면 되는 줄 알았는데 실행시간도 매우 중요하다고 한다. <br>
앞으로는 위에서 언급한 부분들도 잘 신경써가면서 풀어야겠다.<br><br><br>



### 2. [BOJ_19235_모노미노도미노](https://www.acmicpc.net/problem/19235)<br>
[코드](./BOJ_모노미노도미노.cpp)<br>
시간 : 8ms

완전 시뮬레이션 문제.<br>
조건만 잘 따져주면 풀 수 있는 문제.<br>
근데 그 조건 따지는게 정말정말 어려운 문제<br><br>

row or column이 가득찬 경우 해당 행,열을 삭제하므로 블록이 나누어질 수 있다.<br>
이 경우를 제외하고는 블록이 나누어질 수 없다.<br>
이 부분을 따져주지 않아서 계속 틀렸었다.<br><br><br>


### 3. [SWEA_1825_행렬찾기](https://swexpertacademy.com/main/code/problem/problemDetail.do?contestProbId=AV18LoAqItcCFAZN&categoryId=AV18LoAqItcCFAZN&categoryType=CODE)<br>
[코드](./SWEA_행렬찾기.cpp)<br>
시간 : 21ms <br><br>

행과 열의 개수를 구하는 문제<br>
크기가 작은 행렬부터 출력을 해주는데 만약 크기가 같으면 row 개수가 더 작은 순서대로 출력<br>
이 부분 어떻게 해야될 지 몰라서 bubble sort로 풀었다. <br>
종현오빠가 **'비트 마스크'**라는 걸 알려주셔서 정말정말 간단하게 풀 수 있었다. <br>
비교 조건이 2가지 이상일 때 사용하면 좋다 <br>

        int score =(total << 10)+(row << 5) + col ;
        
비교 조건이 전체 크기를 기준으로 먼저 따져주므로 total에는 1024를 곱해주고, 두번째 조건인 row의 개수에 32를 곱해주어 전체 점수를 구할 수 있다.<br>
또한 곱셈 연산자보다 shift 연산이 훨씬 빠르므로 시간도 줄일 수 있다. <br><br><br>

### 4. [BOJ_17825_주사위 윷놀이](https://www.acmicpc.net/problem/17825)<br>
[코드](./BOJ_주사위윷놀이.cpp)<br>
시간 : 12ms <br><br>

문제 조건도 별로 없어서 금방 풀 줄 알았지만 며칠동안 고민했다.<br>
문제 조건도 잘못 이해했었다.<br><br>

1. 움직인 칸에 다른 말이 존재한다면 해당 조합은 아예 무효 ( 움직이지 않는다.) <br>
2. 40의 경우 두 가지 경로에서 올 수 있다.<br>
3. 게임판에 30은 2개 존재<br><br><br>


### 5. [BOJ_17822_원판 돌리기](https://www.acmicpc.net/problem/17822)<br>
[코드](./BOJ_원판돌리기.cpp)<br>
시간 : 4ms <br><br>


시뮬레이션 문제로 문제 조건만 잘 따져주면서 풀면 된다.<br>
모듈화 해서 풀었더니 훨씬 코드가 깔끔하고 디버깅 할 때도 확인하기 쉽다.<br><br>
1. 원판의 번호가 x의 배수인 원판들 회전<br>
2. 인접한 수가 같은 것들을 0으로 바꿔준다. <br>
  ( 이 때 다른 인접한 부분과도 같을 수 있으므로 0으로 바꿔 줄 부분을 tmp 배열에 표시해놓고 모든 원판에 대해 확인해준뒤 map을 update ) <br>
3. 만약 같은 수가 존재하지 않는다면 모든 원판에 대해 평균을 구하고 평균보다 작은 값들은 +1 ,큰 값들은 -1을 해준다.<br>
 평균 구할 때 아래와 같이 하면 <br>

#### sum과 cnt가 int형 변수이므로 avg도 double형이 아니라 int 형이 된다. <br>

 
    double avg = sum/cnt;
 
 
 따라서 아래와 같이 해줘야 된다. ( 이 부분에서 틀렸었다..)<br>

    double avg = double(sum) / double(cnt);


이런 식으로 T번 반복한 뒤 map에 남아있는 값들을 다 더해서 출력해주면 된다. <br><br>

처음에 문제를 잘못 이해해서 시간이 좀 걸렸다.<br> 

