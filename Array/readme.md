#BFS
1. 시간하는 칸을 큐에 넣고 방문했다는 표시를 남김.
2. 큐에서 원소를 꺼내어 저장하고 큐에서 삭제한다.
3. 2번에서 꺼낸 원소에서 **인접하고 방문하지 않은** 원소에 대해 방문했다는 표시를 남기고 해당칸을 큐에 삽입. (인접하지않고 이미 방문한 원소는 무시한다.)
4. 2를 반복한다.

```
int board[101][101];
int visited[101][101];
int dx[4] = {1, 0, -1, 0};
int dy[4] = {0, 1, 0, -1};

int n = 7; int m = 5; // range
queue<pair<int,int>> Q;
vis[0][0] = 1;
Q.push({0, 0});

while(!Q.empty()){
    pair<int, int> cur = Q.front(); Q.pop(); //step 1
    for(int i = 0; i < 4; i++)
    {
        int nx = cur.first + dx[i];
        int ny = cur.first + dy[i];
        if(nx < 0 || nx >= n || ny < 0 || ny >= m) continue;// out of range?

        if(board[nx][ny] == 1 && vis[nx][ny] == 0) // step 3
        {
            vis[nx][ny] = 1; 
            Q.push({nx, ny});
        } 
    } 
}