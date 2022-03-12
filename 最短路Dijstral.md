## 最短路算法之Dijkstral

Dijkstral算法是求解单源最短路的算法，也就是说只能求解从单个起点出发的最短路情况。并且不能处理存在负权边的情况。

### 1.核心思想

Dijkstral算法的核心为贪心算法思想。设起点为s，dis[v]表示从s到v的最短路径，pre[v]为v的前驱节点，用来输出路径。

1.在没有被访问过的节点中寻找一个dis[u]最小的顶点u

2.u标记为已确定最短路径

3.对节点进行松弛，更新与u相连的每个未确定最短路径的顶点v

```java
private int mEdgNum;        // 边的数量
private char[] mVexs;       // 顶点集合
private int[][] mMatrix;    // 邻接矩阵
private static final int INF = Integer.MAX_VALUE;   // 最大值

public static void dijkstral(int start, int prev[], int dist[]) {
    //初始化
    boolean flag[] = new boolean[mVexs.length];
    for (int i = 0;i < mVexs.length;i ++) {
        flag[i] = false;
        prev[i] = -1;
        dist[i] = nMatrix[start][i];
    }
    //初始化起始节点
    flag[start] = true;
    dist[start] = 0;
    //now用于保存当前距离最短的节点
    int now = 0;
    for (int i = 1;i < mVexs.length;i ++) {
        int min = INF;
        //每次都寻找当前距离最短的节点
        for (int j = 0;j < mVexs.length;j ++) {
            if (flag[j] == false && dist[j] < min) {
                min = dist[j];
                now = j;
            }
        }
        //将找到的节点进行设置已访问
        flag[now] = true;
        //对路径进行松弛
        for(int j = 0;j < mVexs.length;j ++) {
            int tmp = nMatrix[now][j] == INF ? INF : min + nMatrix[now][j];
            if (flag[j] == false && tmp < dist[j]) {
                dist[j] = tmp;
                prev[j] = now;
            }
        }
    }
}
```

