# Minimal Cost Spanning Tree
## Kruskal’s algorithm
1. 由小到大排序，所有「邊(Edge)」的權重(Weigh)。

2. 從小到大開始取那些「邊(Edge)」，前提是取到的Edge不能形成一個迴圈(loop, cycle)。

3. 重複步驟 2的動作，直到最後已經不能再取。
## Prim’s algorithm
1. 先從Spanning tree中找一個頂點V作為起始點
2. 找出與V相連且還沒有被選取的頂點裡面加權值最小的邊
3. 並加入與加權值最小的邊相連的頂點
4. 重覆找尋相連且未被選取的頂點加入Spanning tree，直到產生了N-1個邊，將圖的N個頂點連接起來。
## Sollin’s algorithm
1. 每次選擇花費最少的子圖，並且再選取花費較少的邊將這些子圖相連(不能造成循環)，直到邊數為n-1(頂點為n)停止。
# Graph and Shortest Paths
## Dijkstra's algorithm
1. 將所有頂點分為兩個部分：已知最短路徑的頂點集合 P 和未知最短路徑的頂點集合 Q。一開始，P 中只有一個源點為已知點，所以用另一個 book[i] 陣列來將源點做記號為 1，表示在 P 之中為已知。若 book[i] = 0 的話表示這個頂點 i 為未知，還在 Q 之中。
2. 設定源點 s 到自己的最短路徑為 0 (dis[s] = 0)。如果 s 能到其他點 i，則把路徑 e[s][i] 存到 dis[i] 之中。若 s 不能到的頂點，路徑 e[s][i] = ∞。
3. 在集合 Q 中找一個頂點 u 離源點 s 最近，將 u 加入到 P 為已知中。並以 u 為起點對其他邊進行鬆弛，比較從 s → u → v 的路徑能否比 s → v 短，可以的話則更新。
4. 重複步驟 3 直到集合 Q 為 0。最終的 dis 陣列就是源點到所有頂點的最短路徑了。
## Bellman-Ford Algorithm
在演算法中對邊鬆弛的模式和 Dijkstra 演算法一模一樣，但不同的是
不用找出最短距離的確定值，而是用所有頂點的邊的資訊做 n-1 (頂點為 n 個) 輪的鬆弛，這樣就不會像 Dijkstra 演算法中的最短路徑為確定值而無法繼續鬆弛。
## Floyd-Warshall algorithm
【用途】用來解決「有向圖」中，任意兩點間的最短路徑。可以正確處理有「負權」的邊。

【原理】枚舉 + DP
【實作】
枚舉所有中間點 (i)，更新所有【j –> k】的最短路徑。

    dis[j][k] =max(dis[j][i] + dis[i][k],dis[j][k]) 

【複雜度】
時間複雜度：O(N3)
空間複雜度：O(N2)

【範例】ZeroJudge d282: 11015 – 05-2 Rendezvous
【更多練習】TIOJ 1034 . 搶救雷恩大兵 (Saving Ryan)
## Johnson’s Algorithm
时间复杂度为 O(n^2 * log n + nm)
### 想法

若不存在負權，一種找任兩Vertex最短距離的方式為：分別用每個起點跑過一次Dijkstra。

若存在負權但沒有負環(有負環代表永遠沒最短距離)，Johnson提出了一個修改權重的方式，在不改變最短路徑時，同時讓原本的負權邊變為非負權邊。
### 解釋
假設每個點x都存在一個權重h(x)，設新的edge權重為：E_new(a,b)=E(a,b)+h(a)-h(b)

假設任一Dist(x, y)經過若干個節點後，調整後的總權值如下。可以注意到，當起點終點(x, y)沒改變時，不同路徑的總權值相對大小也不變。
## 作法
Johnson's Algorithm 包括以下步骤：

1. 将所有边权加上一个常数 c，使得图中所有边权都为非负数。

2. 使用 Bellman-Ford 算法求出从源点到所有其他点的最短路径。

3. 计算所有边权的修正值 h(u) = d(s, u) - d(s, v)，其中 s 是源点，u 和 v 是边 (u, v) 的两端点。

4. 将所有边权修正为 w'(u, v) = w(u, v) + h(u) - h(v)。
5. 使用 Dijkstra 算法求出从源点到所有其他点的最短路径。
# Activity-on-Edge (AOE) Network