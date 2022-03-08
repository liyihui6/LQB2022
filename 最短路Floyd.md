## 最短路Floyd

最短路径算法-Floyd算法，该算法可解决多源最短路径问题。

1.核心思想：动态规划，不断的对路径进行松弛。

2.图解：

3.代码实现：

```java
public static void main(String args[]) {
    Scanner sc = new Scanner(System.in);
    int n = sc.nextInt(), m = sc.nextInt();
    int map[][] = new int[][];
    Arrays.fill(map, Integer.MAX_VALUE);
    for(int i = 0;i < m;i ++) {
        int node1 = sc.nextInt();
        int node2 = sc.nextInt();
        int road = sc.nextInt();
        map[node1][node2] = road;
    }
    for(int k = 0;k < n;k ++) {
        for(int i = 0;i < n;i ++) {
            for(int j = 0;j < n;j ++) {
                arr[i][j] = Math.min(arr[i][j], arr[i][k] + arr[k+1][j]);
            }
        }
    }
}
```

进阶：若要求解出其最短路径的点，则只需要设置一个path数组来保存中转点即可，随后进行递归迭代。若中转点为-1则最短路径为map\[i][j]

