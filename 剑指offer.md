剑指offer

1. 动态规划     难题
2. 二叉树序列化

**Collection接口常用方法：**

------

|     | 方法                             | 含义                                                                                    |
| --- |:------------------------------ | ------------------------------------------------------------------------------------- |
| 1   | ==add(Object obj)==            |                                                                                       |
| 2   | addAll(Collection coll)        |                                                                                       |
| 3   | ==size()==                     |                                                                                       |
| 4   | clear()                        | void clear():清空集合元素                                                                   |
| 5   | isEmpty()                      |                                                                                       |
| 6   | contains(Object obj)           |                                                                                       |
| 7   | containsAll(Collection coll)   |                                                                                       |
| 8   | ==remove(Object obj)==         |                                                                                       |
| 9   | removeAll(Collection coll)     |                                                                                       |
| 10  | ==retainAll(Collection coll)== | boolean retainAll(Collection c)： 把交集的结果存在当前集合中，不影响c<br/>交集：获取当前集合和coll1集合的交集，并返回给当前集合 |
| 11  | ==equals(Object obj)==         | boolean equals(Object obj)集合是否相等<br/>想返回true，需要当前集合和形参集合的元素都相同。  【并且顺序要一致】            |
| 12  | ==hasCode()==                  | hashCode()获取集合对象的哈希值                                                                  |
| 13  | ==toArray()==                  | Object[] toArray()集合转成对象数组                                                            |
| 14  | ==iterator()==                 | iterator()： 返回迭代器对象，用于集合遍历                                                            |
|     | Collections.sort(list);        |                                                                                       |

**list常用方法：**【记住，必须要掌握熟练使用】
==增：add(Object obj)==

==插：add(int index, Object ele)==  【！！！】

删：==remove(int index)   /    remove(Object obj)==   【注意必须是obj的类型！！】

【ArrayList循环删除元素，要注意只能倒序删除，不能正序删除！否则会产生这种for each写法会发现报出著名的并发修改异常Java.util.ConcurrentModificationException。】

改：set(int index, Object ele)
查：get(int index)

长度：size()
遍历：

​    ① Iterator迭代器方式
​    ② 增强for循环
​    ③ 普通的循环

排序  list1.sort(Comparator c)

list.indexOf(cur)

**数组排序**

1.一维数组：

```java
//方式一
ArrayList<Integer> list2 = new ArrayList<>();
Collections.sort(list2);
//方式二
list2.sort(new Comparator<Integer>() {
    @Override
    public int compare(Integer o1, Integer o2) {
        return 0;
    }
});
```

2.二维数组

```java
//方式一
int[][] arr = new int[n][2];
Arrays.sort(arr, new Comparator<int[]>() {
    @Override
     public int compare(int[] o1, int[] o2) {
         if (o1[0] == o2[0]) return o1[1] - o2[1];
            return o1[0] - o2[0];
     }
});
//方式二
ArrayList<ArrayList<Integer>> list = new ArrayList<>();
list.sort(new Comparator<ArrayList<Integer>>() {
    @Override
    public int compare(ArrayList<Integer> o1, ArrayList<Integer> o2) {
        return 0;
    }
});
```

二维数组

**增加元素：**

```
list.add(new ArrayList<>(Arrays.asList(arr[i][0], arr[i][1])));
```

**list转成数组**

- 一维list转成一维数组

```java 
res.stream().mapToInt(x -> x).toArray();
```

- 二维list转成二维数组

```java
res.toArray(new int[res.size()]);
```











**5.String类常用方法：**
【要记住这些方法！！使用起来更顺手！要熟练掌握，拿起来就使用】
int length()：返回字符串的长度： return value.length
char charAt(int index)： 返回某索引处的字符return value[index]
boolean isEmpty()：判断是否是空字符串：return value.length == 0
String toLowerCase()：使用默认语言环境，将 String 中的所字符转换为小写
String toUpperCase()：使用默认语言环境，将 String 中的所字符转换为大写
String trim()：返回字符串的副本，忽略前导空白和尾部空白 【用户注册的时候，可以对输入的字符串进行去除空白操作】

boolean equals(Object obj)：比较字符串的内容是否相同
boolean equalsIgnoreCase(String anotherString)：与equals方法类似，忽略大小写
String   ==concat==(String str)：将指定字符串连接到此字符串的结尾。 等价于用“+”
==int==   ==compareTo==(==String== anotherString)：比较两个字符串的大小  

【比较内容，重要！返回值！！】

String substring(int beginIndex)：返回一个新的字符串，它是此字符串的从beginIndex开始截取到最后的一个子字符串。
String substring(int beginIndex, int endIndex) ：返回一个新字符串，它是此字符串从beginIndex开始截取到endIndex(不包含)的一个子字符串。

boolean endsWith(String suffix)：测试此字符串是否以指定的后缀结束
boolean startsWith(String prefix)：测试此字符串是否以指定的前缀开始
boolean startsWith(String prefix, int toffset)：测试此字符串从指定索引开始的子字符串是否以指定前缀开始
boolean contains(CharSequence s)：当且仅当此字符串包含指定的 char 值序列时，返回 true  【参数：字符串】
int indexOf(String str)：返回指定子字符串在此字符串中第一次出现处的索引
int indexOf(String str, int fromIndex)：返回指定子字符串在此字符串中第一次出现处的索引，从指定的索引开始
int lastIndexOf(String str)：返回指定子字符串在此字符串中最右边出现处的索引
int lastIndexOf(String str, int fromIndex)：返回指定子字符串在此字符串中最后一次出现处的索引，从指定的索引开始反向搜索

注：indexOf和lastIndexOf方法如果未找到都是返回-1

替换：
String replace(char oldChar, char newChar)：返回一个新的字符串，它是通过用 newChar 替换此字符串中出现的所 oldChar 得到的。
String replace(CharSequence target, CharSequence replacement)：使用指定的字面值替换序列替换此字符串所匹配字面值目标序列的子字符串。
String replaceAll(String regex, String replacement)：使用给定的 replacement 替换此字符串所匹配给定的正则表达式的子字符串。
String replaceFirst(String regex, String replacement)：使用给定的 replacement 替换此字符串匹配给定的正则表达式的第一个子字符串。

匹配:
boolean matches(String regex)：告知此字符串是否匹配给定的正则表达式。

切片：
String[] split(String regex)：根据给定正则表达式的匹配拆分此字符串。
String[] split(String regex, int limit)：根据匹配给定的正则表达式来拆分此字符串，最多不超过limit个，如果超过了，剩下的全部都放到最后一个元素中。

参数2： limit匹配限制
limit的值    含义
大于0    最多匹配limit-1次，次数到了，最后面的作为一个整体返回，数组长度不会超过limit
等于0    一直匹配到结束，但是如果后面全是空串，则丢弃
小于0    一直匹配到结束，不丢弃空串

**4.StringBuffer、StringBuilder中的常用方法**
【掌握！】
增：append(xxx)
删：delete(int start,int end)    【凡是涉及开始和结束的索引，都是左闭右开！！】
改：setCharAt(int n ,char ch) 【修改一个字符】 / replace(int start, int end, String str)
查：charAt(int n )
插：insert(int offset, xxx)
长度：length();
遍历：for() + charAt() / toString()

反转：reverse()

**Arrays工具类中常用的方法**

② Arrays:提供了很多操作数组的方法。

1. boolean equals(int[] a,int[] b)     判断两个数组是否相等。

2. String toString(int[] a)    输出数组信息。

3. void fill(int[] a,int val)    将指定值填充到数组之中。【全部元素被替换成val】

4. void sort(int[] a)   对数组进行排序。==【原数组被改变了，只能是一维数组】== 

5. int binarySearch(int[] a,int key)  对排序后的数组进行二分法检索指定的值。  【返回负数表示未找到指定值！！】

6. Arrays.asList(num[k], num[i], num[j]))  该方法是将数组转化为list

7. ==copyOfRange(int[] original,int from,int to)==
   - original为原始的int型数组，from为开始角标值，to为终止角标值。（其中包括from角标，不包括to角标。即处于[from,to)状态）
   
8. public static int[] ==copyOf(int[] original, int newLength)==
   
   - 使用零复制指定的数组，**截断或填充（如有必要）**，以使副本具有指定的长度。 对于在原始数组和副本中都有效的所有索引，这两个数组将包含相同的值。 对于在副本中有效但不在原件中有效的任何索引，副本将包含`0` 。 当且仅当指定的长度大于原始数组的长度时，这些索引才会存在。

# 链表

**JZ25** **合并两个排序的链表**

```java
public class Solution {
    public ListNode Merge(ListNode list1, ListNode list2) {
        ListNode resList = new ListNode(-1);  // 返回的链表的头节点
        ListNode res = resList;  // 链表的尾节点,用于尾插入

        ListNode p = list1, q = list2;
        while (p != null && q != null) {
            if (p.val < q.val) {
                res.next = p;
                p = p.next;
            } else {
                res.next = q;
                q = q.next;
            }
            res = res.next;
        }
        //将剩余的链表拼在后面

//         if (p != null ) {
//             res.next = p;
//         }
        while (p != null) {
            res.next = p;
            p = p.next;
            res = res.next;
        }
        //直接连接指针
//         if (q != null) {
//             res.next = q;
//         }
        while (q != null) {
            res.next = q;
            q = q.next;
            res = res.next;
        }
        return resList.next;
    }
}
```

**JZ52** **两个链表的第一个==公共结点==**

这道题的意思并不是判断结点值是否相等，而是判断结点是否相等，结点相等意味着**结点值和结点地址**都得相等才行

```
public class Solution {
    public ListNode FindFirstCommonNode(ListNode pHead1, ListNode pHead2) {
        ListNode p1=pHead1;
        ListNode p2=pHead2;
        while (p1 != p2) {
            p1=(p1==null)?pHead2:p1.next;
            p2=(p2==null)?pHead1:p2.next;
        }
        return p1;
    }
}
```

### **JZ23** **链表中环的入口结点**

要求：空间复杂度 O(1)，时间复杂度 O(n)

方式一：快慢指针

如果有环，如何找到这个环的入口
此时我们已经可以判断链表是否有环了，那么接下来要找这个环的入口了

假设从头结点到环形入口节点 的节点数为x。
环形入口节点到 fast指针与slow指针相遇节点 节点数为y。
从相遇节点 再到环形入口节点节点数为 z。 

<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220529165720399.png" alt="image-20220529165720399" style="zoom:67%;" />

那么相遇时：`(x + y) * 2 = x + y + n (y + z)`

两边消掉一个（x+y）: `x + y = n (y + z)`

整理公式之后为如下公式：`x = (n - 1) (y + z) + z `

**当 n为1的时候，公式就化解为 x = z**

这就意味着，从头结点出发一个指针，从相遇节点 也出发一个指针，这两个指针每次只走一个节点， 那么当这两个指针相遇的时候就是 环形入口的节点

也就是在相遇节点处，定义一个指针index1，在头结点处定一个指针index2。让index1和index2同时移动，每次移动一个节点， 那么他们相遇的地方就是 环形入口的节点。

```java
//快慢指针
public ListNode EntryNodeOfLoop(ListNode pHead) {
        if(pHead == null) return null;
        // 定义快慢指针
        ListNode slow = pHead;
        ListNode fast = pHead;
        while(fast != null && fast.next != null){
            // 快指针是满指针的两倍速度
            fast = fast.next.next;
            slow = slow.next;
            // 记录快慢指针第一次相遇的结点
            if(slow == fast) break;
        }
        // 若是快指针指向null，则不存在环
        if(fast == null || fast.next == null) return null;
        // 重新指向链表头部
        fast = pHead;
        // 与第一次相遇的结点相同速度出发，相遇结点为入口结点
        while(fast != slow){
            fast = fast.next;
            slow = slow.next;
        }
        return fast;
    }
```

### **JZ22** **链表中倒数最后k个结点  【难！！！】**

要求：空间复杂度 O(n)，时间复杂度 O(n)

进阶：空间复杂度 O(1)，时间复杂度 O(n)

```java
import java.util.*;
// 方法：快慢指针
public class Solution {
    public ListNode FindKthToTail (ListNode pHead, int k) {
        ListNode left=pHead,right=pHead;
        while(right!=null && k>0){
            right=right.next;
            k--;
        }
        if(k>0) return null;
        while(right!=null){
            right=right.next;
            left=left.next;
        }
        return left;
    }
}
```

### ==**JZ35** **复杂链表的复制  【难！！！】**==

思路：

使用map保存原链表节点，遍历map，构建next和random指针，返回头指针

```java
import java.util.*;
public class Solution {
    public RandomListNode Clone(RandomListNode pHead) {
        RandomListNode cur = pHead;
        HashMap<RandomListNode, RandomListNode> map = new HashMap<>();
        //建立 “原节点 -> 新节点” 的 Map 映射
        while (cur != null) {
            map.put(cur, new RandomListNode(cur.label));
            cur = cur.next;
        }
        //构建新链表的 next 和 random 指向
        cur = pHead;
        while (cur != null) {
            map.get(cur).next = map.get(cur.next);
            map.get(cur).random = map.get(cur.random);
            cur = cur.next;
        }
        //返回新链表的头节点
        return map.get(pHead);
    }
}
```

### ==**JZ76**删除链表中重复的结点==

【这个题有bug！！】

```java
public class Solution {
    public ListNode deleteDuplication(ListNode pHead) {
        if (pHead == null || pHead.next == null) return pHead;
        ListNode dummyHead = new ListNode(0);
        dummyHead.next = pHead;
        //注意遍历范围控制？？
        //一定要注意操作时不能直接拿头结点去操作？？
        ListNode p = dummyHead;
        int x = 0;
        while (p.next != null && p.next.next != null ) {
            if ( p.next.val == p.next.next.val) {
                x = p.next.val;
//                 p.next = p.next.next;
                //如果不写p.next != null那么编译器将会自动检查p.next.next==null?，如果在if中加入p.next != null，那么先判断是否为true
                while (p.next != null && p.next.val == x) {
                    p.next = p.next.next;
                }
            }
            //这种情况无法处理 [1,1]这种！！ 因为p.next.next != null
//             else if (p.next.val == x) {
//                 p.next = p.next.next;
//             }

            else {
                p = p.next;
            }
        }
        return dummyHead.next;
    }
}
```

# 树

### **JZ77** **按之字形顺序打印二叉树**

从哪端进，从哪端出

第一层：从左进左出，第二层：右进右出

~~~java
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        Deque<TreeNode> queue = new LinkedList<>();
        List<List<Integer>> res = new ArrayList<>();
        if(root==null) return res;
        queue.offerLast(root);
        int level = 1;
        while (!queue.isEmpty()) {
            List<Integer> path = new ArrayList<>();
            int size = queue.size();
            for (int i = 0; i < size; i++) {
                if (level % 2 != 0) {
                    TreeNode node = queue.pollFirst();
                    path.add(node.val);
                    if (node.left != null)
                        queue.offerLast(node.left);
                    if (node.right != null)
                        queue.offerLast(node.right);
                } else {
                    TreeNode node = queue.pollLast();
                    path.add(node.val);
                    if (node.right != null)
                        queue.offerFirst(node.right);
                    if (node.left != null)
                        queue.offerFirst(node.left);
                }
            }
            level++;
            res.add(path);
        }
        return res;
    }
}
~~~



**JZ54** **二叉搜索树的第k个节点**

进阶：空间复杂度 O(n)*O*(*n*)，时间复杂度 O(n)*O*(*n*)

时间复杂度 O(N)O(N) ： 当树退化为链表时（全部为右子节点），无论 kk 的值大小，递归深度都为 NN ，占用 O(N)O(N) 时间。
空间复杂度 O(N)O(N) ： 当树退化为链表时（全部为右子节点），系统使用 O(N)O(N) 大小的栈空间。

```
import java.util.*;
public class Solution {

    public int KthNode (TreeNode proot, int k) {
        ArrayList<Integer> list = new ArrayList<>();
        if (proot == null || k == 0 )
            return -1;
        preOrder(proot, list);
        if (k > list.size())
            return -1;
        Collections.sort(list);
        return list.get(k - 1);
    }

    public void preOrder(TreeNode root, ArrayList list) {
        if (root != null) {
            list.add(root.val);
            preOrder(root.left, list);
            preOrder(root.right, list);
        }
    }
}
```

### ==**JZ26** **树的子结构**==

1. 判断根节点是否重合
   1. 如果重合，判断左右子树是否对应
2. 否则左子树中是否包含子结构，
3. 右子树是否包含子结构

```java
public class Solution {
    public boolean HasSubtree(TreeNode root1,TreeNode root2) {
         //特例处理
        if (root1 == null || root2 == null) return false;
//         分为三种情况：1 根节点比较，2.和左子树比较，3.和右子树比较
        return isSame(root1, root2) || HasSubtree(root1.left, root2) ||
               HasSubtree(root1.right, root2);
    }

      public boolean isSame(TreeNode root1, TreeNode root2) {
        //终止条件 root2为空，表示越过叶节点，B树匹配完成
        if (root2 == null) return true;
        //root1为空，表示越过叶节点，匹配失败
        if (root1 == null || root1.val != root2.val) return false;

        return isSame(root1.left, root2.left) && isSame(root1.right, root2.right);
    }
}
```

### **==JZ33 二叉搜索树的后序遍历序列==**

要求：空间复杂度 O(n)，时间时间复杂度 O(n^2)

 方法一：递归分治

递归解析：
<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220511114405295.png" alt="image-20220511114405295" style="zoom: 67%;" />

<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220511114818249.png" alt="image-20220511114818249" style="zoom:67%;" />

<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220511115228477.png" alt="image-20220511115228477" style="zoom: 50%;" />

```java
public class Solution {
    public boolean VerifySquenceOfBST(int [] sequence) {
        if (sequence.length == 0) return false;
        return recur(sequence, 0, sequence.length - 1);
    }

    public boolean recur(int [] sequence, int l, int r) {
        //终止条件 当前树只有一个节点
        if (l >= r) return true;
        //递推工作
        int pos = l;
        while (sequence[p] < sequence[r])pos++;
        //第一个右子树节点
        int mid = pos;
        //继续向后遍历 判断右子树
        while (sequence[pos] > sequence[r]) pos++;

        return pos == r && recur(sequence, l, mid - 1)  && recur(sequence, mid, r - 1);
    }
}
```

### **JZ34** **二叉树中和为某一值的路径(二)**

```java
import java.util.ArrayList;
public class Solution {
    ArrayList<ArrayList<Integer>> res = new ArrayList<>();
    ArrayList<Integer> path = new ArrayList<>();
    public ArrayList<ArrayList<Integer>> FindPath(TreeNode root, int expectNumber) {
        //终止条件
        if (root == null) return res;

        //递推工作
        expectNumber -= root.val;
        path.add(root.val);
        if (expectNumber == 0 && root.left == null && root.right == null) {
            res.add(new ArrayList(path));
        }
        FindPath(root.left, expectNumber);
        FindPath(root.right, expectNumber);
        //注意此处？？
        path.remove(path.size() - 1);
        return res;
    }
}
```

### ==**JZ8** **二叉树的下一个结点  【记公式！！！】**==

要求：空间复杂度 O(1)  ，时间复杂度 O(n)

结合图，我们可发现分成两大类：

1、当前节点有右子树的，那么下个结点就是右子树最左边的点；

2、当前节点没有右子树的，也可以分成两类：

​    a)当前节点是父节点左孩子，那么父节点就是下一个节点 ；

​    b)当前节点是父节点的右孩子找他的父节点的父节点的父节点...直到当前结点是其父节点的左孩子位置。如果没有，那么他就是尾节点。

```java
public class Solution {
    public TreeLinkNode GetNext(TreeLinkNode pNode) {
        //1、有右子树的，那么下个结点就是右子树最左边的点；
        if (pNode.right != null) {
            TreeLinkNode node = pNode.right;
            while (node.left != null)
                node = node.left;
            return node;
        } else {
            while (pNode.next != null) {
                TreeLinkNode parent = pNode.next;
                //a)是父节点左孩子，那么父节点就是下一个节点 ；
                if (parent.left == pNode)
                    return parent;
                //b)是父节点的右孩子找他的父节点的父节点的父节点...直到当前结点是其父节点的左孩子位置尾节点。
                pNode = parent;
            }
        }
        return null;
    }
}
```



### **JZ84** **二叉树中和为某一值的路径(三)**

```java
import java.util.*;
public class Solution {
    int res = 0;
    public int FindPath (TreeNode root, int sum) {
        if(root==null) return res;
        recur(root, sum);
        FindPath(root.left, sum);
        FindPath(root.right, sum);
        return res;
    }
    public void recur(TreeNode root, int sum) {
        //终止条件
        if (root == null) return ;

        //递推工作
        sum -= root.val;
        if (sum == 0)
            res += 1;
        recur(root.left, sum);
        recur(root.right, sum);
    }
}
```

### [剑指 Offer 36. ==二叉搜索树==与双向链表](https://leetcode.cn/problems/er-cha-sou-suo-shu-yu-shuang-xiang-lian-biao-lcof/)

==时间复杂度 O(N)== ： N为二叉树的节点数，中序遍历需要访问所有节点。
空间复杂度 O(N) ： 最差情况下，即树退化为链表时，递归深度达到 N，系统使用 O(N)栈空间。

本文解法基于性质：二叉搜索树的**中序遍历为 递增序列** 。
将 二叉搜索树 转换成一个 “排序的循环双向链表” ，其中包含三个要素：

**排序链表**： 节点应从小到大排序，因此应使用 中序遍历 “从小到大”访问树的节点。
**双向链表**： 在构建相邻节点的引用关系时，设前驱节点 pre 和当前节点 cur ，不仅应构建 pre.right = cur ，也应构建 cur.left = pre 。
**循环链表**： 设链表头节点 head 和尾节点 tail ，则应构建 head.left = tail 和 tail.right = head 。！！

~~~java
class Solution {
    Node head, pre;
    public Node treeToDoublyList(Node root) {
        if(root==null) return null;
        dfs(root);
        
		//head 指向头节点， pre 指向尾节点，位置可以交换
        pre.right = head;
        head.left =pre;
        return head;
    }

    public void dfs(Node cur){
        if(cur==null) return;
        
        dfs(cur.left);
        //pre用于记录双向链表中位于cur左侧的节点，即上一次迭代中的cur,当pre==null时，cur左侧没有节点,即此时cur为双向链表中的头节点！！
        if(pre==null) head = cur;
        //pre!=null时，cur左侧存在节点pre，需要进行pre.right=cur的操作。
        else 
            pre.right = cur;
       //pre是否为null对这句没有影响,且这句放在上面两句if else之前也是可以的。
        cur.left = pre;
        pre = cur;//pre指向当前的cur
        dfs(cur.right);//全部迭代完成后，pre指向双向链表中的尾节点
    }
}
~~~

### [剑指 Offer 54. 二叉搜索树的第k大节点](https://leetcode.cn/problems/er-cha-sou-suo-shu-de-di-kda-jie-dian-lcof/)



```cs
class Solution {
    int count = 0;
    int res = 0;
    public int kthLargest(TreeNode root, int k) {
        recur(root, k);
        return res;
    }
    private void recur(TreeNode root, int k) {
        if (root == null) return;

        recur(root.right, k);
        if (++count == k) res = root.val;
        recur(root.left, k);
    }
}
```

# 队列 & 栈

### **JZ31** **栈的压入、弹出序列**

考虑借用一个辅助栈 stack，**模拟** 压入 / 弹出操作的排列。根据是否模拟成功，即可得到结果。

入栈操作： 按照压栈序列的顺序执行。
出栈操作： 每次入栈后，循环判断 “栈顶元素 == 弹出序列的当前元素” 是否成立，将符合弹出序列顺序的栈顶元素全部弹出。

```java
import java.util.*;
public class Solution {
    public boolean IsPopOrder(int [] pushA, int [] popA) {
        Stack<Integer> stack = new Stack<>();
        int i = 0;
        for (int num : pushA) {
            stack.push(num);
            while (!stack.isEmpty() && popA[i] == stack.peek()) {
                stack.pop();
                i++;
            }
        }
        return stack.isEmpty();
    }
}
```

### **JZ59** **滑动窗口的最大值   【难！！】**

思路：双端队列

队列中的元素按照从大到小排序，如果新增加的元素值>队尾元素，则依次删除，直到保证队列元素的从大到小顺序。

如果队列中元素个数超过size，则从队首删除；

如果元素个数达到size，则将队列中队首元素作为最大值加到res中

```java
import java.util.*;
public class Solution {
    public ArrayList<Integer> maxInWindows(int [] num, int size) {
        ArrayList<Integer> res = new ArrayList<>();
        Deque<Integer> deque = new LinkedList<>();
        for (int i = 0; i < num.length; i++) {
            while (!deque.isEmpty() && num[deque.peekLast()] < num[i]) {
                deque.pollLast();
            }
            deque.addLast(i);
            // 计算窗口左侧边界
            // 当队首元素的下标小于滑动窗口左侧边界left时
            // 表示队首元素已经不再滑动窗口内，因此将其从队首移除
            if (i - deque.peekFirst() >= size)
                deque.pollFirst();
            if (i + 1 >= size)
                res.add(num[deque.peekFirst()]);
        }
        return res;
    }
}
```

### [面试题59 - II. 队列的最大值](https://leetcode.cn/problems/dui-lie-de-zui-da-zhi-lcof/)

Deque存储最大值，Queue存储数据

~~~java
class MaxQueue {
    Queue<Integer> queue;
    Deque<Integer> deque;
    public MaxQueue() {
        queue = new LinkedList<>();
        deque = new LinkedList<>();
    }

    public int max_value() {
        return deque.isEmpty() ? -1 : deque.peekFirst();
    }

    public void push_back(int value) {
        queue.offer(value);
        while (!deque.isEmpty() && deque.peekLast() < value) {
            deque.pollLast();
        }
        deque.offerLast(value);
    }

    public int pop_front() {
        if (queue.isEmpty()) return -1;
        if (queue.peek().equals(deque.peekFirst())) {
            deque.pollFirst();
        }
        return queue.poll();
    }
}
~~~



# 搜索算法

### ==JZ53  数字在升序数组中出现的次数==

要求：空间复杂度 O(1)，时间复杂度 O(logn)

解题思路：

> ==排序数组中的搜索问题==，首先想到 **二分法** 解决。

本题要求统计数字 target的出现次数，可转化为：使用二分法分别找到 左边界 left 和 右边界 rightright ，易得数字 target 的数量为 right - left - 1

<img src="https://pic.leetcode-cn.com/b4521d9ba346cad9e382017d1abd1db2304b4521d4f2d839c32d0ecff17a9c0d-Picture1.png" alt="Picture1.png" style="zoom: 50%;" />

```
//二分查找
public class Solution {
    public int GetNumberOfK(int [] array, int k) {
        int low = 0, high = array.length-1;
        //查找右边界
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (array[mid] <= k)
                low = mid + 1;
            else
                high = mid - 1;
        }
        int right = low; //right=4位置！！

        //查找左边界
        low=0;high=array.length-1;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (array[mid] < k)
                low = mid + 1;
            else
                high = mid - 1;
        }
        int left = high;  // left=2位置
        return right-left-1;
    }
}
```

**JZ4** **二维数组中的查找**

题解三： 线性搜索

复杂度分析:
时间复杂度:*O(M+N)*
空间复杂度:*O(1)*

```
public class Solution {
    public boolean Find(int target, int [][] array) {
        int rows = array.length, cols = array[0].length;
        int i = 0, j = cols-1;
        while (i < rows && j >= 0) {
            if (target < array[i][j]) {
                j--;
            } else if (target > array[i][j]) {
                i++;
            } else {
                return true;
            }
        }
        return false;
    }
}
```

### ==**JZ11** **旋转数组的最小数字**==

主要思路：
1.数组可以分为两个有序的子数组。其中，左排序的数组的值大于右排序数组中的值。

2.声明left,right 分别指向数组的左右两端；

3.mid = (left+right) / 2 为二分的中间位置。
4.mid，left,  right分为三种情况：
	a. nums[mid] > nums[right]时， 那么 最小值一定在 [mid+1,right]区间中；
	b.nums[mid] < nums[right]时，那么最小值一定在[left,mid]区间内。
	c. nums[mid] = nums[right]时，==无法判断最小值在哪个区间，所以此时只能缩小right的值。==

<img src="https://pic.leetcode-cn.com/1608987739-vGDKDN-file_1608987739110" alt="微信图片_20201226204725" style="zoom: 50%;" />

```java
class Solution {
    public int minArray(int[] nums) {
        int n = nums.length;
        int left = 0;
        int right = n - 1;
        while (left < right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] > nums[right]) {
                left = mid + 1;
            } else if (nums[mid] < nums[right]) {
                //注意下标！！
                right = mid ;
            } else {
                right--;
            }
        }
        return nums[left];
    }
}
```

### ==**JZ44** **数字序列中某一位的数字   【×  难】**==

<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220510155417187.png" alt="image-20220510155417187" style="zoom: 33%;" />

时间复杂度O(logn) ：
空间复杂度 O(logn) ：

```java
import java.util.*;
public class Solution {
    public int findNthDigit (int n) {
        int digit = 1;   //位数
        long start = 1;   //起始范围
        long count = 9;   //每个范围中的数字位数
        //1. 确定所求数字的起始范围和位数
        while (n - count > 0) {
            n -= count;
            digit += 1;
            start *= 10;
            count = 9 * start * digit;
        }
        //2. 确定所求数位所在的数字
        long num = start + (n - 1) / digit;

        //3. 确定所求数位在 num的哪一数位
        int inx = (n - 1) % digit;
        return String.valueOf(num).charAt(inx) - '0';
    }
}
```

### [剑指 Offer 57. 和为s的两个数字](https://leetcode.cn/problems/he-wei-sde-liang-ge-shu-zi-lcof/)

注意有序数组的双指针处理方式，体悟！！



~~~java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;
        while (left < right) {
            int sum = nums[left] + nums[right];
            if (sum == target) {
                return new int[]{nums[left], nums[right]};
            } else if (sum < target) {
                left++;
            } else {
                right--;
            }
        }
        return new int[0];
    }
}
~~~

### [剑指 Offer 57 - II. 和为s的连续正数序列](https://leetcode.cn/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/)

滑动窗口：

~~~java
class Solution {
    public int[][] findContinuousSequence(int target) {
        //左右和总和   i是左边界值 j是右边界值 s是和
        int i = 1, j = 2, s = 3;
        //结果集
        List<int[]> res = new ArrayList<>();
        //窗口左右
        while(i < j) {
            //如果和为目标值 添加到结果集
            if(s == target) {
                //数组长度为右边界-左边界+1
                int[] ans = new int[j - i + 1];
                //从左边界循环到右边界 循环添加 左值到右值
                for(int k = i; k <= j; k++)
                    ans[k - i] = k;
                res.add(ans);
            }
            //如果窗口和大于等于目标值说明 窗口溢出或者窗口到达 
            //缩减 去掉最左边的值
            if(s >= target) {
                s -= i;
                i++;
            } else {
                //如果小于目标值说明窗口未到达 扩张添加右值
                j++;
                s += j;
            }
        }
        return res.toArray(new int[0][]);
~~~



# 动态规划

三种时间复杂度算法求解斐波那契数列

1. 递归法：时间复杂度 ![[公式]](https://www.zhihu.com/equation?tex=O%282%5En%29)
2. 循环法（DP）：时间复杂度  O(n)     
3. 矩阵连乘法：时间复杂度 ![[公式]](https://www.zhihu.com/equation?tex=O%281%29) (？有待商榷)





### ==**JZ85** **连续子数组的最大和(二)   【细节 ？？】**==

要求: 时间复杂度O(n)，空间复杂度O(n)

进阶: 时间复杂度O(n)，空间复杂度O(1)

​		但是题目要求需要返回长度最长的一个，我们则每次用left、right记录该子数组的起始，需要更新最大值的时候（要么子数组和更大，要么子数组和相等的情况下区间要更长）顺便更新最终的区间首尾，最后根据区间首尾获取子数组。

<img src="https://uploadfiles.nowcoder.com/images/20211204/397721558_1638607774484/83C9DB1D7BB98AFD16716153916EAC03" alt="alt" style="zoom:50%;" />

```java
import java.util.*;
public class Solution {
    public int[] FindGreatestSumOfSubArray (int[] array) {
        int n = array.length;
        int[] dp = new int[n];
        dp[0] = array[0];
        int left = 0;
        int start = 0, end = 1;
        int max = -102;
        for (int i = 1; i < n; i++) {
            if (dp[i - 1] >= 0) {
                dp[i] = dp[i - 1] + array[i];
            } else {
                dp[i] = array[i];
                left = i;
            }
            if (dp[i] >= max) {
                max = dp[i];
                start = left;
                end = i + 1;
            }
        }
        return Arrays.copyOfRange(array, start, end );
    }
}


import java.util.*;
public class Solution {
    public int[] FindGreatestSumOfSubArray (int[] array) {
        int n = array.length;
        int cur = array[0];
        int left = 0;
        int start = 0, end = 1;
        int max = -102;
        for (int i = 1; i < n; i++) {
            if (cur >= 0) {
                cur += array[i];
            } else {
                cur = array[i];
                left = i;
            }
            if (cur >= max) {
                max = cur;
                start = left;
                end = i + 1;
            }
        }
        return Arrays.copyOfRange(array, start, end );
    }
}
```

### ==**JZ19** **正则表达式匹配  【×  难！！！】**==

f[i] [j] 代表 str 的前 i 个和 pattern 的前 j 个能否匹配

**转移方程**

  对于前面两个情况，可以合并成一种情况 f[i] [j]=f[i−1] [j−1]
  对于第三种情况，对于 c* 分为看和不看两种情况
    不看：直接砍掉正则串pattern 的后面两个， f[i] [j]=f[i] [j−2]
    看：正则串pattern 不动，主串str前移一个，f[i] [j]=f[i−1] [j]

时间复杂度：O(mn)，其中 m 和 n分别是字符串 s和 p的长度。我们需要计算出所有的状态，并且每个状态在进行转移时的时间复杂度为 O(1)

空间复杂度：O(mn)，即为存储所有状态使用的空间。

<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220510110526692.png" alt="image-20220510110526692" style="zoom:67%;" />

<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220510115051070.png" alt="image-20220510115051070" style="zoom: 50%;" />

| 是字符*要么出现0次，要么出现多次，所以结果带或！！

//注意此处dp和s[]和p[]的下标！！

```java
import java.util.*;
public class Solution {
    public boolean match (String str, String pattern) {
        int m = str.length();
        int n = pattern.length();
        char[] s = str.toCharArray();
        char[] p = pattern.toCharArray();
        boolean[][] dp = new boolean[m + 1][n + 1];

        for (int i = 0; i <= m; i++) {
            for (int j = 0; j <= n; j++) {
                //p是空串
                if (j == 0) {
                    if (i == 0)
                        dp[i][j] = true;
                }
                //p是非空串，需要讨论分析
                else {
                    //p是字母或者.
                    if (p[j - 1] != '*') {
                        //注意要加括号！！
                        if (i>=1 && (s[i - 1] == p[j - 1] || p[j - 1] == '.'))
                            dp[i][j] = dp[i - 1][j - 1];
                    }
                    //p是*
                    else {
                        //*前字符重复0次，不出现
                        if (j >= 2)
                            dp[i][j] |= dp[i][j - 2];
                        //*前字符重复多次，出现
                        if (i>=1 && j >= 2 && (s[i-1] == p[j - 2] || p[j - 2] == '.'))
                            dp[i][j] |= dp[i - 1][j];
                    }
                }
            }
        }
        return dp[m][n];
    }
}
```

**JZ71** **跳台阶扩展问题**

**题解一：递归**
题解思路：考虑最后一步是跳几阶到达目标位置的。
主要分析：
1.令f(n)表示n阶台阶总的跳法
2.假设最后只跳一步，那么f(n) = f(n-1); 最后跳两步，那么f(n) = f(n-2)；以此类推，可知总的跳法为f(n) = f(n-1) + f(n-2) +....+f(0)

f(n)=f(n-1)+f(n-2)+f(n-3)+...+f(n-n)

**复杂度分析：**
时间复杂度：*O(N^N)*
空间复杂度：*O(N) : 递归栈深度*

**题解三： 动态规划+**
题解思路：延续题解一中的公式f(n) = f(n-1) + f(n-2) +....+f(0)
分析：
1.知道f(n) = f(n-1) + f(n-2) +....+f(0)，那么f(n-1) = f(n-2) + f(n-3) +......+f(0);
2.可知 f(n) = 2 * f(n-1);
3.初始ans = 1;
复杂度分析：
时间复杂度：*O(N)*，从1~n依次遍历了台阶数
空间复杂度：*O(1)*，没有申请其他空间存放数据

```
public class Solution {
    public int jumpFloorII(int target) {
        //为啥为1？
        //f(2)=f(1)+f(0)=2
//         if(target==0) return 1;
//         int res=0;
//         for (int i = 0; i < target; i++) {
//             res+=jumpFloorII(i);
//         }
//         return res;

        if (target == 0) return 1;
        if (target == 1) return 1;
        int res = 1;
        for (int i = 2; i <= target; i++)
            res = 2 * res;
        return res;
    }
}
```

**JZ70** **矩形覆盖**

进阶：空间复杂度 O(1) ，时间复杂度 O(n)

==时间复杂度：O（n）==

空间复杂度：O（1）

f[n] = f[n-1] + f[n-2]

```java
public class Solution {
    public int rectCover(int target) {
        //递归方式
//         if(target==0) return 0;
//         if(target==1) return 1;
//         if(target==2) return 2;

//         return rectCover(target-1)+rectCover(target-2);

        //迭代方式
        if (target <= 2) return target;
        int m = 1, n = 2, res = 0;
        for (int i = 3; i <= target; i++) {
            res = m + n;
            m = n;
            n = res;
        }
        return res;
    }
}
```

3. 

**JZ63** **买卖股票的最好时机(一)**

dp[i] [0]表示卖出股票，不持有股票时的最大收益

dp[i] [1]表示买入股票，持有股票时的最大收益

**推导状态转移方程：**
dp[i] [0]：规定了今天不持股，有以下两种情况：
  昨天不持股，今天什么都不做；
  昨天持股，今天卖出股票（现金数增加），

  状态转移方程：dp[i] [0] = Math.max(dp[i - 1] [0], dp[i - 1] [1] + prices[i]);
dp[i][1]：规定了今天持股，有以下两种情况：
  昨天持股，今天什么都不做（现金数与昨天一样）；
  ==昨天不持股，今天买入股票（注意：只允许交易一次，因此手上的现金数就是当天的股价的相反数）==

  状态转移方程：==dp[i] [1] = Math.max(dp[i - 1] [1], -prices[i]);==

```
import java.util.*;
public class Solution {

    public int maxProfit (int[] prices) {
        int n = prices.length, minVal = prices[0];
        int[][] dp=new int[n][2];
        dp[0][0]=0;
        dp[0][1]=-prices[0];
        for(int i=1;i<n;i++){
            dp[i][0]=Math.max(dp[i-1][0],dp[i-1][1]+prices[i]);
            //买入股票之前不能卖出股票
            dp[i][1]=Math.max(dp[i-1][1],-prices[i]);
        }
        return dp[n-1][0];
    }
}
```

**JZ47** **礼物的最大价值**

```
import java.util.*;
public class Solution {
    public int maxValue (int[][] grid) {
        int m = grid.length, n = grid[0].length;
        int[][] dp = new int[m][n];
        dp[0][0]=grid[0][0];
        for (int i = 1; i < m; i++) {
            dp[i][0]=dp[i-1][0]+grid[i][0];
        }
        for (int j = 1; j < n; j++) {
            dp[0][j]=dp[0][j-1]+grid[0][j];
        }
        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                dp[i][j]=Math.max(dp[i-1][j],dp[i][j-1])+grid[i][j];
            }
        }
        return dp[m-1][n-1];
    }
}
```

### ==**JZ48** **最长不含重复字符的子字符串 【难！！！】**==

方法一：动态规划

1. dp[i]表示==i位置==的不含重复字符的最长字符串长度

2. ==公式==   【不懂？？】
   
   总共两种情形：
   
   1. 字符没有出现过，长度加一；
   
   2. 字符出现过：此时又有两种情况：
      
      - 这个字符上一次出现的位置没有算在在当前最长不重复子串上，例如：dfafbsdas，遍历到第二个a时，第一个a不在最长不重复子串上，所以长度也是直接加一；  f(n) = f(n - 1) + 1
      
      - 这个字符上一次出现的位置算在在当前最长不重复子串上，例如：fabsdas，遍历到第二个a时，当前位置的长度重新计算为两个重复字符之间的距离，就是bsda；    f(n) = index - lastIndex

3. 初始化

   dp[i]=1

   方法三：双指针 + 哈希表

<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220509164303238.png" alt="image-20220509164303238" style="zoom:50%;" />

<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220509164323081.png" alt="image-20220509164323081" style="zoom: 50%;" />

```java
import java.util.*;
public class Solution {
    HashMap<Character, Integer> map = new HashMap<>();
    public int lengthOfLongestSubstring (String s) {
        int n = s.length();
        int res = 0, left = -1;
        for (int right = 0; right < n; right++) {
            if (map.containsKey(s.charAt(right))) {
                left = Math.max(left, map.get(s.charAt(right)));
            }
            map.put(s.charAt(right), right);
            res = Math.max(res, right - left);
        }
        return res;
    }
}

import java.util.*;
public class Solution {
    public int lengthOfLongestSubstring (String s) {
        HashMap<Character, Integer> map = new HashMap<>();
        int n = s.length();
        int[] dp = new int[n];
        dp[0] = 1;
        int res = 1;
        map.put(s.charAt(0),0);
        for (int i = 1; i < n; i++) {
            char ch = s.charAt(i);
            if (map.containsKey(ch)) {
                dp[i] = Math.min(dp[i - 1] + 1, i - map.get(ch));
            } else {
                dp[i] = dp[i - 1] + 1;
            }
            map.put(ch, i);
            res = Math.max(res, dp[i]);
        }
        return res;
    }
}
```

### ==**JZ46** **把数字翻译成字符串**==

1、dp[i]：表示长度为i的字符串有多少种不同的翻译方法

2、dp公式：

两位子串>11  &&   两位子串>25：

​	dp[i] = dp[i - 1] + dp[i - 2];

否则：

​	dp[i] = dp[i - 1];

```java
class Solution {
    public int translateNum(int num) {
        String strs = String.valueOf(num);
        int n = strs.length();
        int[] dp = new int[n + 1];
        dp[0] = 1;
        dp[1] = 1;
        for (int i = 2; i < n + 1; i++) {
            String number = strs.substring(i - 2, i);
            if (number.compareTo("10") >= 0 && number.compareTo("25") <= 0) {
                dp[i] = dp[i - 1] + dp[i - 2];
            } else
                dp[i] = dp[i - 1];
        }
        return dp[n];
    }
}
```

### [==剑指 Offer 49. 丑数！！！==](https://leetcode.cn/problems/chou-shu-lcof/)

求按从小到大的顺序的第 n 个丑数

![image-20220508133747335](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220508133747335.png)

<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220503105539647.png" alt="image-20220503105539647" style="zoom:67%;" />

<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220503105524434.png" alt="image-20220503105524434" style="zoom: 60%;" />

习惯上我们把1当做是第一个丑数。

~~~java
public class Solution {
    public int GetUglyNumber_Solution(int index) {
        if (index == 0) return 0;
        int[] dp = new int[index + 1];
        dp[1] = 1;
        int p2 = 1, p3 = 1, p5 = 1;
        for (int i = 2; i <= index; i++) {
            int num2 = dp[p2] * 2;
            int num3 = dp[p3] * 3;
            int num5 = dp[p5] * 5;
            dp[i] = Math.min(Math.min(num2, num3), num5);
            if (dp[i] == num2) p2++;
            if (dp[i] == num3) p3++;
            if (dp[i] == num5) p5++;
        }
        return dp[index];
    }
}
~~~

### [剑指 Offer 60. n个骰子的点数](https://leetcode.cn/problems/nge-tou-zi-de-dian-shu-lcof/)

```java
dp五部曲:假设投掷n个骰子总的投的次数为6^n
1.状态定义:dp[i][j]为投掷i个骰子点数和为j的次数
2.状态转移:dp[i][j]由dp[i-1][j-1],dp[i-1][j-2],...,dp[i-1][j-6]相加得到
	因此dp[i][j]=∑dp[i-1][j-k],其中1<=k<=6&&j-k>=i-1(j-k<i-1时dp[i][j]=0)
	举例:dp[2][4]=dp[1][3]+dp[1][2]+dp[1][1],dp[1][0]=0,投1次点数和不可能为0
	最本质的就是每当n+1,游戏规模会扩大6倍,也就是在6^n-1次的基础上重复玩了6个6^n-1次
	因此dp[i][j]的次数可以为dp[i-1][j-k]次数的和,而第n次玩的点数k为1-6概率相等
	因此对应dp[i-1][j-k]中重复的6次6^n-1每次选出dp[i-1][j-1],dp[i-1][j-2],进行相加即就是转移过来的玩6^n次的dp[i][j]的次数
3.初始化:只需要初始化dp[1][i]=1即可(1<=i<=6)
4.遍历顺序:显然dp[i]是需要dp[i-1]推导的,而dp[i][j]是需要dp[i-1][j-k]推导，因此j的遍历顺序没关系
5.返回形式:将这5*n+1种出现的次数/6^n就是答案
```

~~~java 
class Solution {
    public double[] dicesProbability(int n) {
        // i的范围是[1,n],j的范围是[n,6n]
        int[][] dp = new int[n + 1][6 * n + 1];

        // 初始化dp[i][1]=1,因为投1次出现的次数都为1
        for(int i = 1; i <= 6; i++) {
            dp[1][i] = 1;
        }

        // 遍历每个状态,i还需遍历[2,n]
        for(int i = 2; i <= n; i++) {
            // j的范围是[i,6i]
            for(int j = i; j <= 6 * i; j++) {
                // k的范围为1 <= k <= 6 && j - k >= i - 1
                for(int k = 1; k <= 6; k++) {
                    if(j - k < i - 1) break;
                    // dp[i][j]的值为∑dp[i-1][j-k]
                    dp[i][j] += dp[i - 1][j - k];
                }
            }
        }
        
        // 总的次数为6^n
        double all = Math.pow(6, n);
        // 可能出现的点数为5*n+1种
        double[] res = new double[5 * n + 1];
        for(int j = n; j <= 6 * n; j++) {
            // 向左偏移n位输出
            res[j - n] = dp[n][j] / all;
        }
        return res;
    }
}
~~~



### ==**JZ62** **孩子们的游戏(圆圈中最后剩下的数)**==

https://blog.csdn.net/u011500062/article/details/72855826

时间复杂度：O(n)，需要求解的函数值有 n 个。

空间复杂度：O(n)，函数的递归深度为 n，需要使用 O(n) 的栈空间。

法一：递归(推荐使用)

实际上，本题是著名的 “约瑟夫环” 问题，可使用动态规划解决。

![image-20220508160428891](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220508160428891.png)

<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220508160354854.png" alt="image-20220508160354854" style="zoom:67%;" />

方式二：迭代

复杂度分析

- 时间复杂度：O(n)，需要求解的函数值有 n 个。
- 空间复杂度：O(1)，只使用常数个变量。

```java 
public class Solution {
    public int LastRemaining_Solution(int n, int m) {
		//if (n == 1)
		//	return 0;
		//return (LastRemaining_Solution(n - 1, m) + m) % n;

        int f = 0;
        for (int i = 2; i <= n; i++) {
            f = (f + m) % i;
        }
        return f;
    }
}
```



# 回溯

### ==**JZ12** **矩阵中的路径**==

```java
import java.util.*;
public class Solution {
    public boolean hasPath (char[][] matrix, String word) {
        boolean[][] visited = new boolean[matrix.length][matrix[0].length];
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[0].length; j++) {
                boolean flag = backTracking(matrix, visited, i, j, word, 0);
                if (flag)
                    return true;
            }
        }
        return false;
    }
    //右 下  左  上
    int[][] directions = {{0, 1},  {1, 0}, {0, -1}, {-1, 0}};
    public boolean backTracking(char[][] matrix, boolean[][] visited, int i, int j,
                                String s, int k) {
        if (matrix[i][j] != s.charAt(k))
            return false;
        else if (k == s.length() - 1)
            return true;

        boolean res = false;
        visited[i][j] = true;
        for (int[] dir : directions) {
            int newi = i + dir[0], newj = j + dir[1];
            if (newi >= 0 && newi < matrix.length && newj >= 0 && newj < matrix[0].length) {
                if (!visited[newi][newj]) {
                    boolean flag = backTracking(matrix, visited, newi, newj, s, k + 1);
                    if (flag) {
                        res = true;
                        break;
                    }
                }
            }
        }
        visited[i][j] = false;
        return res;
    }
}



import java.util.*;

public class Solution {
    int m, n;
    public boolean hasPath (char[][] matrix, String word) {
        char[] words = word.toCharArray();
        m = matrix.length;
        n = matrix[0].length;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (dfs(matrix, words, i, j, 0))
                    return true;
            }
        }
        return false;
    }

    public boolean dfs(char[][] matrix, char[] words, int i, int j, int k) {
        if (i < 0 || j < 0 || i >= m || j >= n || matrix[i][j] != words[k])
            return false;
        if (k == words.length - 1) return true;

        matrix[i][j] = '0';
        boolean res = dfs(matrix, words, i, j + 1, k + 1) ||
                      dfs(matrix, words, i + 1, j, k + 1) || dfs(matrix, words, i, j - 1, k + 1)
                      || dfs(matrix, words, i-1, j, k + 1) ;
        matrix[i][j] = words[k];
        return res;



    }
}
```

## DFS

### ==**JZ13** **机器人的运动范围**==

方法一：深度优先遍历 DFS
可以理解为暴力法模拟机器人在矩阵中的所有路径。DFS 通过递归，先朝一个方向搜到底，再回溯至上个节点，沿另一个方向搜索，以此类推。
剪枝： 在搜索中，遇到数位和超出目标值、此元素已访问，则应立即返回，称之为 可行性剪枝 
算法解析：
递归参数： 当前元素在矩阵中的行列索引 i 和 j ，两者的数位和 si, sj 。
终止条件： 当 ① 行列索引越界 或 ② 数位和超出目标值 k 或 ③ 当前元素已访问过 时，返回 00 ，代表不计入可达解。
递推工作：
标记当前单元格 ：将索引 (i, j) 存入 Set visited 中，代表此单元格已被访问过。
搜索下一单元格： 计算当前元素的 下、右 两个方向元素的数位和，并开启下层递归 。
回溯返回值： 返回 1 + 右方搜索的可达解总数 + 下方搜索的可达解总数，代表从本单元格递归搜索的可达解总数。

```java
class Solution {
    int row;
    int col;
    boolean[][] visited;
    int res = 0;
    public int movingCount(int m, int n, int k) {
        row = m;
        col = n;
        visited = new boolean[row][col];
        // 不需要循环！！
        dfs(0, 0, k);
        return res;
    }

    private void dfs(int i, int j, int k) {
        int sum = i / 10 + i % 10 + j / 10 + j % 10;
        if (i < 0 || i >= row || j < 0 || j >= col || sum > k || visited[i][j]) return;

        visited[i][j] = true;
        res++;
        dfs(i, j + 1, k);
        dfs(i, j - 1, k);
        dfs(i + 1, j, k);
        dfs(i - 1, j, k);
    }
}
```

### [剑指 Offer 38. 字符串的排列](https://leetcode.cn/problems/zi-fu-chuan-de-pai-lie-lcof/)

注意去重的方式！！

~~~java
class Solution {
    boolean[] visited;
    ArrayList<String> res = new ArrayList<>();
    StringBuilder path = new StringBuilder();

    public String[] permutation(String s) {
        int n = s.length();
        visited = new boolean[n];
        char[] arr = s.toCharArray();
        Arrays.sort(arr);
        backTrack(arr);
        return res.toArray(new String[0]);
    }

    private void backTrack(char[] arr) {

        if (path.length() == arr.length) {
            res.add(path.toString());
        }

        for (int i = 0; i < arr.length; i++) {
            if (visited[i]) continue;
            // 去重！！
            if (i > 0 && visited[i - 1] && arr[i] == arr[i - 1]) continue;

            visited[i] = true;
            path.append(arr[i]);
            backTrack(arr);
            path.deleteCharAt(path.length() - 1);
            visited[i] = false;
        }
    }
}
~~~







# 排序

### [剑指 Offer 03. 数组中重复的数字](https://leetcode.cn/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/)

在一个长度为 n 的数组 nums 里的所有数字都在 **0～n-1** 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

方法二：原地交换

遍历中，第一次遇到数字 xx 时，将其交换至索引 xx 处；而当第二次遇到数字 xx 时，一定有 nums[x] = xnums[x]=x ，此时即可得到一组重复数字。

时间复杂度 O(N)
空间复杂度 O(1)

<img src="https://pic.leetcode-cn.com/1618146573-bOieFQ-Picture0.png" alt="Picture0.png" style="zoom: 33%;" />

~~~java
class Solution {
    public int findRepeatNumber(int[] nums) {
        HashSet<Integer> set = new HashSet<>();
        int res = 0;
        for (int num : nums) {
            if (set.contains(num)) {
                res = num;
            } else {
                set.add(num);
            }
        }
        return res;
    }
}



class Solution {
    public int findRepeatNumber(int[] nums) {
        int res = 0;
        int n = nums.length;
        int i = 0;
        while (i < n) {
            int inx = nums[i];
            // 正确位置
            if (inx == i) {
                i++;
                continue;
            }
            // 重复数字
            if (nums[inx] == inx) {
                return inx;
            }
            // 非重复数字
            else {
                nums[i] = nums[inx];
                nums[inx] = inx;
            }
        }
        return -1;
    }
}
~~~

### [剑指 Offer 40. 最小的k个数](https://leetcode.cn/problems/zui-xiao-de-kge-shu-lcof/)

解题思路：
对于经典TopK问题，本文给出 4 种通用解决方案。
**一、用快排+切分最最最高效解决 TopK 问题：**

这里说的快排，应该是利用了快排思想的快速选择

快排切分时间复杂度分析： 因为我们是要找下标为k的元素，第一次切分的时候需要遍历整个数组 (0 ~ n) 找到了下标是 j 的元素，假如 k 比 j 小的话，那么我们下次切分只要遍历数组 (0~k-1)的元素就行啦，反之如果 k 比 j 大的话，那下次切分只要遍历数组 (k+1～n) 的元素就行啦，总之可以看作每次调用 partition 遍历的元素数目都是上一次遍历的 1/2，因此时间复杂度是 ==N + N/2 + N/4 + ... + N/N = 2N, 因此时间复杂度是 O(N)==

~~~java
//方式一
class Solution {
    public int[] getLeastNumbers(int[] arr, int k) {
        if(k==0) return new int[0];
        int n = arr.length;
        return quickSort(arr, 0, n - 1, k);
    }

    private int[] quickSort(int[] arr, int l, int r, int k) {
        int pivot = arr[l];
        int left = l;
        int right = r;

        while (left < right) {
            while (left < right && arr[right] >= pivot) right--;
            arr[left] = arr[right];
            while (left < right && arr[left] <= pivot) left++;
            arr[right] = arr[left];
        }
        arr[left] = pivot;
        if (left > k - 1) {
            return quickSort(arr, l, left - 1, k);
        } else if (left < k - 1) {
            return quickSort(arr, left + 1, r, k);
        }else
            return Arrays.copyOfRange(arr, 0, left + 1);
    }
}
~~~

**二、大根堆(前 K 小) / 小根堆（前 K 大)**
本题是求前 K 小，因此用一个容量为 K 的大根堆，每次 poll 出最大的数，那堆中保留的就是前 K 小啦（注意不是小根堆！小根堆的话需要把全部的元素都入堆，那是 O(NlogN)，就不是 O(NlogK)）

~~~java 
// 保持堆的大小为K，然后遍历数组中的数字，遍历的时候做如下判断：
// 1. 若目前堆的大小小于K，将当前数字放入堆中。
// 2. 否则判断当前数字与大根堆堆顶元素的大小关系，如果当前数字比大根堆堆顶还大，这个数就直接跳过；
//    反之如果当前数字比大根堆堆顶小，先poll掉堆顶，再将该数字放入堆中。
class Solution {
    public int[] getLeastNumbers(int[] arr, int k) {
        if (k == 0 || arr.length == 0) {
            return new int[0];
        }
        // 默认是小根堆，实现大根堆需要重写一下比较器。
        Queue<Integer> pq = new PriorityQueue<>((v1, v2) -> v2 - v1);
        for (int num: arr) {
            if (pq.size() < k) {
                pq.offer(num);
            } else if (num < pq.peek()) {
                pq.poll();
                pq.offer(num);
            }
        }
        
        // 返回堆中的元素
        int[] res = new int[pq.size()];
        int idx = 0;
        for(int num: pq) {
            res[idx++] = num;
        }
        return res;
    }
}


~~~



# 位运算

### [剑指 Offer 16. 数值的整数次方](https://leetcode.cn/problems/shu-zhi-de-zheng-shu-ci-fang-lcof/)

快速幂

https://leetcode.cn/problems/shu-zhi-de-zheng-shu-ci-fang-lcof/solution/jian-dan-li-jie-kuai-su-mi-by-ollieq-rl74/

![image-20220831131814875](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220831131814875.png)

~~~java
class Solution {
    public double myPow(double x, int n) {
        if(x == 0) return 0;
        long b = n;
        double res = 1.0;
        if(b < 0) {
            x = 1 / x;
            b = -b;
        }
        while(b > 0){
            // 最后一位为1，需要乘上该位上的权重
            if((b & 1) == 1){
                res *= x;
            }
            x *= x;
            b >>= 1;
        }
        return res;
    }
}
~~~



### ==**JZ65** **不用加减乘除做加法**==

进阶：空间复杂度 O(1)，时间复杂度 O(1)

使用位运算实现加法。

```java
public class Solution {
    public int Add(int num1, int num2) {
        //无进位和等于异或结果   进位等于与结果左移一位
        int sum = num1 ^ num2;
        int carry = (num1 & num2) << 1;
        while (carry != 0) {
            int a = sum;
            int b = carry;
            sum = a ^ b;
            carry = (a & b) << 1;
        }
        return sum;
    }
}
```

### ==**JZ15** **二进制中1的个数**==

```java
// >>>无符号右移，不管正数还是负数，高位都用0补齐(忽略符号位)
// >>，有符号右移位，将运算数的二进制整体右移指定位数，整数高位用0补齐，负数高位用1补齐(保持负数符号不变)。
public class Solution {
    public int NumberOf1(int n) {
        int count = 0;
        while (n != 0) {
            count += (n & 1);
            n >>>= 1;
        }
        return count;
    }
}
```

### ==**JZ56** **数组中只出现一次的两个数字！！**==

要求：空间复杂度 O(1)，时间复杂度 O(n)

**简化问题：** 一个整型数组 `nums` 里除 **一个** 数字之外，其他数字都出现了两次。

当只有一个出现了一次的数字的时候，则只需要将全部数进行异或运算，运算结果就剩下了那个只出现一次的数字了。



假设数组异或的二进制结果为10010，那么说明这两个数从右向左数第2位是不同的

**那么可以根据数组里面所有数的第二位为0或者1将数组划分为2个。**

这样做可以将目标数必然分散在不同的数组中，而且相同的数必然落在同一个数组中。

这两个数组里面的数各自进行异或，得到的结果就是答案

```java
public int[] singleNumber(int[] nums) {
    int x = 0;
    for(int num : nums)  // 1. 遍历 nums 执行异或运算
        x ^= num;
    return x;            // 2. 返回出现一次的数字 x
}
```

```java
class Solution {
    public int[] singleNumbers(int[] nums) {
        int n = nums.length;
        int s = 0;
        for (int num : nums) {
            s ^= num;
        }
        
        int m = 1;
        while ((s & m) == 0) {
            m <<= 1;
        }

        int x = 0;
        int y = 0;
        for (int num : nums) {
            if ((num & m) != 0) {
                x ^= num;
            } else
                y ^= num;
        }
        return new int[]{x, y};
    }
}
```

### [剑指 Offer 56 - II. 数组中数字出现的次数 II](https://leetcode.cn/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-ii-lcof/)

方法二：遍历统计

​		考虑数字的二进制形式，对于出现三次的数字，各 二进制位 出现的次数都是 3 的倍数。因此，统计所有数字的各二进制位中 1的出现次数，并对 3求余，结果则为只出现一次的数字。

<img src="https://pic.leetcode-cn.com/28f2379be5beccb877c8f1586d8673a256594e0fc45422b03773b8d4c8418825-Picture1.png" alt="Picture1.png" style="zoom: 33%;" />



~~~java
class Solution {
    public int singleNumber(int[] nums) {
        int[] bits = new int[32];
        int res = 0;
        int n = nums.length;
        for (int i = 0; i < n; i++) {
            int j = 0;
            while (nums[i] != 0) {
                bits[j] += nums[i] & 1;
                nums[i] >>>= 1;
                j++;
            }
        }

        for (int i = 0; i < 32; i++) {
            int bit = bits[i] % 3;
            res += bit * (1 << i);
        }
        return res;
    }
}
~~~



### ==**JZ64** **求1+2+3+...+n**==

进阶： 空间复杂度 O(1) ，时间复杂度 O(n)

```java
class Solution {
    int res = 0;

    public int sumNums(int n) {
        boolean x = n > 1 && sumNums(n - 1) > 0;
        res += n;
        return res;
    }
}
```

# 模拟

### [剑指 Offer 29. 顺时针打印矩阵](https://leetcode.cn/problems/shun-shi-zhen-da-yin-ju-zhen-lcof/)



~~~java
class Solution {
    public int[] spiralOrder(int[][] matrix) {
        int row = matrix.length;
        if(row==0) return new int[]{};
        int col = matrix[0].length;
        ArrayList<Integer> res = new ArrayList<>();
        int num = row * col;
        int top = 0;
        int left = 0;
        int bottom = row - 1;
        int right = col - 1;

        while (num >= 1) {
            for (int j = left; j <= right && num >= 1; j++) {
                res.add(matrix[top][j]);
                num--;
            }
            top++;
            for (int i = top; i <= bottom && num >= 1; i++) {
                res.add(matrix[i][right]);
                num--;
            }
            right--;
            for (int j = right; j >= left && num >= 1; j--) {
                res.add(matrix[bottom][j]);
                num--;
            }
            bottom--;
            for (int i = bottom; i >= top && num >= 1; i--) {
                res.add(matrix[i][left]);
                num--;
            }
            left++;
        }
        return res.stream().mapToInt(x -> x).toArray();
    }
}
~~~



### ==**JZ61** **扑克牌顺子  【巧！！！】**==

要求：空间复杂度 O(1)，时间复杂度 O(nlogn)，本题也有时间复杂度 O(n)的解法

根据题意，此 5 张牌是顺子的 充分条件 如下：

- 除大小王外，所有牌 无重复 ；
- 设此 5张牌中最大的牌为 max ，最小的牌为 min （大小王除外），则需满足：
  max - min < 5

复杂度分析：
时间复杂度O(NlogN)=O(5log5)=O(1) ： 其中 N为 nums 长度，本题中N=5 ；数组排序使用 O(NlogN) 时间。
空间复杂度 O(1) ： 变量joker 使用 O(1) 大小的额外空间。

```java
import java.util.*;
public class Solution {
    public boolean IsContinuous(int [] numbers) {
        int n = numbers.length;
        int queen=0;
        Arrays.sort(numbers);
        for (int i = 0; i < n-1; i++) {
            if(numbers[i]==0) queen++;
            else if(numbers[i+1]==numbers[i])
                return false;
        }
        return numbers[n-1]-numbers[queen]<5;
    }
}
```

### ==**JZ67** **把字符串转换成整数(atoi)**==

方法一：遍历法（推荐使用）<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220502174052257.png" alt="image-20220502174052257" style="zoom:60%;" />

```java
import java.util.*;
public class Solution {
    public int StrToInt (String s) {
        int index = 0;
        int n = s.length();
        int res = 0;

        while (index < n) {
            if (s.charAt(index) == ' ')
                index++;
            else break;
        }
        if (index == n)
            return 0;

        int sign = 1;
        if (s.charAt(index) == '+')
            index++;
        else if (s.charAt(index) == '-') {
            index++;
            sign = -1;
        }
        if (index == n)
            return 0;
        while (index < n && s.charAt(index)<='9' && s.charAt(index)>='0') {
            char ch = s.charAt(index);
            if (res > (Integer.MAX_VALUE -(ch-'0'))/10)
                return sign == 1 ? Integer.MAX_VALUE : Integer.MIN_VALUE;
            res = res * 10 + (ch-'0');

            index++;
        }
        return res*sign;
    }
}
```

### ==**JZ20** **表示数值的字符串 【难！！！】**==

进阶：时间复杂度O(n) ，空间复杂度O(n)

 解题思路：

~~~java
 * 分析：整体分两种
 * A[.[B]][e|EC]   .B[e|EC]
 * 
 * A：整数，可正可负
 * B：整数，只能正
 * C：整数，可正可负
     
数字的格式可以用A[.[B]][e|EC]或者.B[e|EC]表示
其中A和C都是整数（可以有正负号，也可以没有），而B是一个无符号整数
总共有三种形式  A[.[B]][e|EC]    .B[e|EC]     A[e|EC]
~~~



```java
class Solution {
    int index;
    int n;

    public boolean isNumber(String s) {
        n = s.length();
        if (n == 0) return false;
        index = 0;

        while (index < n && s.charAt(index) == ' ') {
            index++;
            if (index == n) return false;
        }
        // 判断小数之前的部分
        boolean isNum = scanInteger(s);
        if (index < n && s.charAt(index) == '.') {
            index++;
            // 判断小数之后的部分
            isNum = scanUnsignedInteger(s) || isNum ;
        }
       
        if (index < n && (s.charAt(index) == 'e' || s.charAt(index) == 'E')) {
            index++;
            isNum = isNum && scanInteger(s);
        }
        while (index < n && s.charAt(index) == ' ') {
            index++;
            if (index == n) break;
        }
        return index == n && isNum;
    }

    // 判断带符号整数
    private boolean scanInteger(String s) {
        if (index < n && (s.charAt(index) == '-' || s.charAt(index) == '+')) {
            index++;
        }
        return scanUnsignedInteger(s);
    }

    // 判断无符号整数
    private boolean scanUnsignedInteger(String s) {
        int cur = index;
        while (index < n && s.charAt(index) >= '0' && s.charAt(index) <= '9') {
            index++;
        }
        return index > cur;
    }

}
```

# 数组

### ==**JZ21** **调整数组顺序使奇数位于偶数前面(一)**==

要求：时间复杂度 O(n)，空间复杂度 O(n)

**进阶：时间复杂度 O(n^2)，空间复杂度 O(1)**

方式二：快慢指针

```java
class Solution {
        public int[] exchange(int[] nums) {
        int n = nums.length;
        int right = 0;
        int left = 0;
        while (right < n) {
            if (nums[right] % 2 != 0) {
                swap(nums, left, right);
                left++;
            }
            right++;
        }
        return nums;
    }

    private void swap(int[] nums, int left, int right) {
        int tmp = nums[left];
        nums[left] = nums[right];
        nums[right] = tmp;
    }
}
```

### ==**JZ81** **调整数组顺序使奇数位于偶数前面(二)**==

思想：快慢指针。

```java
import java.util.*;

public class Solution {

    public int[] reOrderArrayTwo (int[] array) {
        int n = array.length;
        for (int i = 0, j = 0; i < n; i++) {
            if (array[i] % 2 != 0) {
                int tmp = array[i];
                array[i] = array[j];
                array[j++] = tmp;
            }
        }
        return array;
    }
}
```

### ==**JZ39** **数组中出现次数超过一半的数字**==

方式一：

==空间复杂度：O(1)，时间复杂度 O(n)==

**摩尔投票法**（Boyer–Moore majority vote algorithm），也被称作「多数投票法」，算法解决的问题是：如何在任意多的候选人中（选票无序），选出获得票数最多的那个。
算法可以分为两个阶段：
**对抗阶段**：分属两个候选人的票数进行两两对抗抵消
**计数阶段**：计算对抗结果中最后留下的候选人票数是否有效

**思想**：【擂主和擂主的个数！！】

候选人(cand_num)初始化为nums[0]，票数count初始化为1。
当遇到与cand_num相同的数，则票数count = count + 1，否则票数count = count - 1。
当票数count为0时，更换候选人，并将票数count重置为1。
遍历完数组后，cand_num即为最终答案。

```java
import java.util.*;
public class Solution {
    public int MoreThanHalfNum_Solution(int [] array) {
        int n = nums.length;
        // candidate擂主
        int candidate = nums[0];
        // 表示擂台上擂主的个数
        int count = 1;
        // 数组中的所有数字开始轮番上擂台进行挑战，每个数字的战斗力均为 1
        // 1、相同势力的数字可以都停留在擂台上
        // 2、不同势力的数字会同归于尽
        for (int i = 1; i < n; i++) {
            // 擂台上没有擂主时,那么当前arr[i]就是擂主
            if (count == 0)
                candidate = nums[i];
            //如果擂台上有擂主，而且和当前擂主同类，则votes+1，否则votes-2
            if (nums[i] == candidate) {
                count++;
            } else {
                count--;
            }
        }
        return candidate;
    }
}
```

### ==**JZ43** **整数中1出现的次数**==

进阶：空间复杂度 O(1) ，时间复杂度 O(lognn)

思路：数位dp

<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220507114245535.png" alt="image-20220507114245535" style="zoom: 50%;" />

```java
class Solution {
    public int countDigitOne(int n) {
        int res = 0;
        int base = 1;
        int a = n / 10;
        int b = 0;
        int cur = n % 10;
        while (base<=n) {

            if (cur > 1) {
                res += (a + 1) * base;
            } else if (cur < 1) {
                res += a * base;
            } else {
                res += a * base + (b + 1);
            }

            b += cur * base;
            cur = a % 10;
            a = a / 10;
            base *= 10;
        }
        return res;
    }
}


public class Solution {
    public int NumberOf1Between1AndN_Solution(int n) {
        int res = 0;
        int base = 1;
        while (base <= n) {
            int a = n / base / 10;
            int b = n % base;
            int cur = n / base % 10;
            if (cur > 1) {
                res += (a + 1) * base;
            } else if (cur == 1) {
                res += a * base + b + 1;
            } else {
                res += a * base;
            }
            base *= 10;
        }
        return res;
    }
}
```

### ==**JZ45** **把数组排成最小的数**==

 **方法一：重载比较的排序（推荐使用）**

**具体做法：**

- step 1：优先判断空数组的特殊情况。

- step 2：将数组中的数字元素转换成字符串类型。

- step 3：重载排序比较为字符串类型的x + y < y + x，然后进行排序。

- step 4：将排序结果再按照字符串拼接成一个整体。
  
  复杂度分析：
  
  时间复杂度 O(NlogN) ： N 为 nums数组的长度 ；使用内置函数的平均时间复杂度为 O(NlogN) ，最差为 O(N 2 ) 。
  空间复杂度 O(N) ： 字符串数组 nums占用线性大小的额外空间。
  
  <img src="https://upload-images.jianshu.io/upload_images/7038163-24dc6f1251b6c745.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp" alt="img" style="zoom: 200%;" />

```java
public class Solution {
    public String PrintMinNumber(int [] numbers) {
        int n = numbers.length;
        if (numbers.length == 0)
            return "";

        String[] nums = new String[numbers.length];
        for (int i = 0; i < n; i++) {
            // nums[i]=String.valueOf(numbers[i]);
            nums[i] = numbers[i] + "";
        }
        //根据指定比较器产生的顺序对指定对象数组进行排序。
        //此处比较器对象中的泛型和下面参数的类型是一致的，
        //如果不指定泛型，那么下面的参数使用具体类型，会报错
        //nums也是string类型
        //注意要想自定义排序规则，就不能使用基本数据类型int,double ,char
        Arrays.sort(nums, new Comparator<String>() {
            public int compare(String s1, String s2) {
                //compareTo属于字符串方法
                return (s1 + s2).compareTo(s2 + s1);
            }
        });
        StringBuilder res = new StringBuilder();
        for (int i = 0; i < n; i++) {
            res.append(nums[i]);
        }
        return res.toString();
    }
}
```

### ==**JZ49** **丑数**==

<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220503102340141.png" alt="image-20220503102340141" style="zoom: 50%;" />

```java
class Solution {
    public boolean isUgly(int n) {
        if (n<=0)
            return false;
        int[] facotrs={2,3,5};
        for (int facotr : facotrs) {
            while (n%facotr==0){
                n=n/facotr;
            }
        }
        return n==1;
    }
}
```

```
class Solution {
    // 有序数组直接二分
    public int missingNumber(int[] nums) {
        int left = 0, right = nums.length - 1;
        // 下雨等于
        while(left <= right) {
            // 防溢出的写法，位运算提速，这里注意位运算的优先级问题，需要用括号括起来
            int mid = left + ((right - left) >> 1);
            if(nums[mid] == mid) left = mid + 1;
            else right = mid - 1;
        }
        return left;
    }
}
```

### [剑指 Offer 53 - II. 0～n-1中缺失的数字](https://leetcode.cn/problems/que-shi-de-shu-zi-lcof/)

```java
class Solution {
    // 有序数组直接二分
    public int missingNumber(int[] nums) {
        int left = 0, right = nums.length - 1;
        // 下雨等于
        while(left <= right) {
            // 防溢出的写法，位运算提速，这里注意位运算的优先级问题，需要用括号括起来
            int mid = left + ((right - left) >> 1);
            if(nums[mid] == mid) left = mid + 1;
            else right = mid - 1;
        }
        return left;
    }
}
```

### ==**JZ74** **和为S的连续正数序列**==

方法二：滑动窗口（双指针）

```java
import java.util.ArrayList;
public class Solution {
    public ArrayList<ArrayList<Integer> > FindContinuousSequence(int sum) {
        ArrayList<ArrayList<Integer>> res = new ArrayList<>();
        int i = 1, j = 2, s = 3;
        while (i < j) {
            if (s == sum) {
                ArrayList<Integer> tmp = new ArrayList<>();
                for (int k = i; k <= j; k++) {
                    tmp.add(k);
                }
                res.add(tmp);
            }
            if (s > sum) {
                s -= i;
                i++;
            } else {
                j++;
                s += j;

            }
        }
        return res;

    }
}


import java.util.*;
public class Solution {
    public ArrayList<ArrayList<Integer> > FindContinuousSequence(int sum) {
        ArrayList<ArrayList<Integer>> res = new ArrayList<>();
        int i = 1, j = 2;
        int s = 3;
        while (i <= sum / 2) {
            if (s == sum) {
                ArrayList<Integer> tmp = new ArrayList<>();
                for (int k = i; k <= j; k++) {
                    tmp.add(k);
                }
                res.add(tmp);
                s -= i;
                i++;
            } else if (s < sum) {
                j++;
                s += j;
            } else {
                s -= i;
                i++;
            }
        }
        return res;
    }
}
```

### ==**JZ57** **和为S的两个数字**==

```java
import java.util.*;
public class Solution {
    public ArrayList<Integer> FindNumbersWithSum(int [] array, int sum) {
        ArrayList<Integer> res = new ArrayList<>();
        HashMap<Integer, Integer> map = new HashMap();
        int n = array.length;
        for (int i = 0; i < n; i++) {
            //注意此处的操作！！
            int num = sum - array[i];
            if (!map.containsKey(num)) {
                map.put(array[i], i);
            } else {
                res.add(num);
                res.add(array[i]);
                break;
            }
        }
        return res;
    }
}
```

**JZ58** **左旋转字符串**

方法一：三次反转（推荐使用）

~~~
class Solution {
    public String reverseLeftWords(String s, int k) {
        int n = s.length();
        char[] chars = s.toCharArray();
        reverse(chars, 0, n - 1);
        reverse(chars, 0, n - k - 1);
        reverse(chars, n - k, n-1);
        return new String(chars);
    }

    private void reverse(char[] arr, int i, int j) {
        while (i < j) {
            char tmp = arr[i];
            arr[i] = arr[j];
            arr[j] = tmp;
            i++;
            j--;
        }
    }
}
~~~

**JZ75** **字符流中第一个不重复的字符**

方法一：哈希表+字符串（推荐使用）

**具体做法：**

- step 1：准备一个字符串来记录输入的字符流，用哈希表统计每个字符的次数，二者都是全局变量。
- step 2：在Insert函数中对输入的字符，加到字符串最后，然后统计出现次数。
- step 3：在FirstAppearingOnce函数遍历该字符串，对于每个字符查找哈希表，返回第一个计数为1的字符，如果遍历完字符串以后都没，则返回#。

### **JZ14** **剪绳子**

进阶：空间复杂度 O(1)，时间复杂度 O(n)

方法一：动态规划（推荐使用）

用dp[i]表示==长度为i==的绳子可以被剪出来的==最大乘积==

dp[i] = Math.max(dp[i], Math.max(j * (i - j), j * dp[i - j]));

解题思路：

1、我们想要求长度为n的绳子剪掉后的最大乘积，可以从前面比n小的绳子转移而来
2、用一个dp数组记录从0到n长度的绳子剪掉后的最大乘积，也就是dp[i]表示长度为i的绳子剪成m段后的最大乘积，初始化**dp[2] = 1**
3、我们先把绳子剪掉第一段（长度为j），如果只剪掉长度为1，对最后的乘积无任何增益，所以从长度为2开始剪
4、剪了第一段后，剩下(i - j)长度可以剪也可以不剪。如果不剪的话长度乘积即为j * (i - j)；如果剪的话长度乘积即为j * dp[i - j]。取两者最大值max(j * (i - j), j * dp[i - j])
5、第一段长度j可以取的区间为[2,i)，对所有j不同的情况取最大值，因此最终dp[i]的转移方程为dp[i] = max(dp[i], max(j * (i - j), j * dp[i - j]))
6、最后返回dp[n]即可

**复杂度分析：**

- 时间复杂度：O(n^2)，两层遍历
- 空间复杂度：O(n)，辅助数组dp的空间

~~~java
class Solution {
    public int cuttingRope(int n) {
        int[] dp = new int[n + 1];
        dp[2] = 1;
        // 绳子长度
        for (int i = 3; i < n + 1; i++) {
            // 段数
            for (int j = 1; j < i; j++) {
                dp[i] = Math.max(dp[i], Math.max(j * (i - j), j * dp[i - j]));
            }
        }
        return dp[n];
    }
}
~~~



方法二：贪心（扩展思路）

进阶：空间复杂度 O(1)，时间复杂度 O(n)

<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220508180549781.png" alt="image-20220508180549781" style="zoom:150%;" />

**具体做法：**

- step 1：按照上述思路，不超过3的直接计算
- step 2：超过3的不断累乘3，然后number不断减去3，直到最后不超过4。
- step 3：最后乘上剩余的数字。

```java

import java.util.*;
public class Solution {
    public int cutRope (int n) {
        //不超过3直接计算
        if(n <= 3)
            return n - 1;
        //4比较特殊！！
        if(n==4) return 4;
        int res=1;
        while(n>4){
            res*=3;
            n-=3;
        }
        return res*n;
    }
}
```

### ==**JZ83** **剪绳子（进阶版）**==

进阶：空间复杂度 O(1) ， 时间复杂度 O(logn)

方法一：快速幂+快速乘法

<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220831101346779.png" alt="image-20220831101346779" style="zoom:150%;" />

**快速幂**

<img src="https://uploadfiles.nowcoder.com/images/20220420/397721558_1650427629432/D2B5CA33BD970F64A6301FA75AE2EB22" alt="alt" style="zoom: 33%;" />

```java
class Solution {
    int mod = 1000000007;
    public int cuttingRope(int n) {
        if (n <= 3) return n - 1;
        int a = n / 3;
        int b = n % 3;
        if (b == 0) {
            return (int) (pow(3, a) % mod);
        } else if (b == 1) {
            return (int) (2 * 2 * pow(3, a - 1) % mod);
        } else {
            return (int) (2 * pow(3, a) % mod);
        }
    }

    // 非递归形式的快速幂
    public long pow(long base, int count) {
        long res = 1;
        while (count > 0) {
            if ((count & 1) == 1) {
                res = (res * base) % mod;
            }
            base = (base * base) % mod;
            count >>= 1;
        }
        return res;
    }
}
```

## 字符串

### [剑指 Offer 58 - I. 翻转单词顺序](https://leetcode.cn/problems/fan-zhuan-dan-ci-shun-xu-lcof/)

~~~
class Solution {
    public static String reverseWords(String s) {
        String[] strs = s.trim().split(" ");
        int n = strs.length;
        String res = "";
        for (int i = n - 1; i >= 0; i--) {
            if (strs[i].equals("")) continue;
            res += strs[i];
            if (i != 0)
                res += " ";
        }
        return res;
    }
}
~~~





## 总结

1.牛客剑指offer刷过3遍，过了几个月效果不好！！

2.力扣剑指offer刷过1遍



