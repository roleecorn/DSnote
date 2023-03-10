# Sorting
## Insertion Sort 
插入排序法(Insertion Sort)，原理是
1. 逐一將原始資料加入已排序好資料中
2. 並逐一與已排序好的資料作比較，找到對的位置插入。

例如:已有2筆排序好資料，將第3筆資料與前面已排序好的2筆資料作比較，找到對的位置插入，再將第4筆資料與前面已排序好的3筆資料作比較，找到對的位置插入，以此類推。
## Quick Sort 
程式時間複雜度 Ｏ(NlogN)

快速排序 (Quick Sort) 的想法是說，
1. 先找一個基準點
2. 然後派兩個代理人分別從資料的兩邊開始往中間找
3. 如果右邊找到一個值比基準點小，左邊找到一個值比基準點大
4. 就讓他們互換。
5. 反覆找並互換，直到兩個人相遇。然後再將相遇的點跟基準點互換。第一輪結束。
## Merge Sort 
合併排序法(Merge Sort)原理是會
1. 先將原始資料分割成兩個資料列，接著再將兩個資料繼續分割成兩個資料列，依此類推，直到無法再分割，也就是每組都只剩下一筆資料時
2. 再兩兩合併各組資料，合併時也會進行該組排序，每次排序都是比較最左邊的資料，將較小的資料加到新的資料列中
3. 依此類推，直到最後合併成一個排序好的資料列為止。
## Heap Sort 
若以升序排序說明，把陣列轉換成最大堆積（Max-Heap Heap），這是一種滿足最大堆積性質（Max-Heap Property）的二元樹：對於除了根之外的每個節點i, A[parent(i)] ≥ A[i]。

重複從最大堆積取出數值最大的結點（把根結點和最後一個結點交換，把交換後的最後一個結點移出堆積），並讓殘餘的堆積維持最大堆積性質。

![RUNOOB 图标](https://upload.wikimedia.org/wikipedia/commons/1/1b/Sorting_heapsort_anim.gif)
## Radix Sort 
Radix sort 基本特性如下：

整數排序法：以整數作為排序的鍵值。

分配式排序法：不透過兩兩比較，而是分析鍵值分佈來排序。特定情況下可達線性執行時間。

穩定性：採用 LSD 的 Radix sort 屬穩定排序法（Stable sort）；透過優化，採用 MSD 也可以是穩定排序法。

簡單的 LSD Radix sort 步驟如下：

1. LSD of each key：取得每個資料鍵值的最小位數（LSD）。
2. Sorting subroutine：依據該位數大小排序資料。
3. Repeating：取得下一個有效位數，並重複步驟二，至最大位數（MSD）為止。
## External Sorting