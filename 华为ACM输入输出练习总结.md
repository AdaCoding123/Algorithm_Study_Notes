# ACM之输入输出

​		由于ACM竞赛题目的输入数据和输出数据一般有多组（不定），并且格式多种多样，所以，如何处理题目的输入输出是对大家的一项最基本的要求。这也是困扰初学者的一大问题。

## **一、Java**

### **1. 输入:**

```java
2
12 A tidy tiger tied a tie tighter to tidy her tiny tail
1 a
16 A big black bug bit a big black bear made the big black bear bleed blood
2 b?? b???

2
20 8
1 2 3 2 6 5 2 1
17 10
1 4 5 7 10 8 7 17 2 8
    
4
1
```

- 读一个整数：int n = sc.==nextInt();==   【以空格分隔！！】
  - Scans the ==next token of the input== as an int.
    An invocation of this method of the form nextInt() behaves in exactly the same way as the invocation nextInt(radix), where radix is the default radix of this scanner.
    Returns:
    the int scanned from the input
    Throws:
    InputMismatchException – if the next token does not match the Integer regular expression, or is out of range
    NoSuchElementException – if input is exhausted
    IllegalStateException – if this scanner is closed

- 读一个字符串：String s = sc.==next();==（以空格作为分隔符） 【】

- 读一个浮点数：double t =sc.==nextDouble();==

- 读一整行：String s = sc.==nextLine();== 
  - Advances this scanner past the current line and ==returns the input that was skipped==. This method returns the rest of the current line, excluding any line separator at the end. The position is set to the beginning of the next line

- 判断是否有下一个输入可以用sc.hasNext()或sc.hasNextInt()或sc.hasNextDouble()或sc.hasNextLine()
  - hasNext()方法判断输入（文件、字符串、键盘等输入流）==是否还有下一个输入项==，若有，返回true，反之false。



| 返回类型 | 方法         | 描述                                           |
| :------- | ------------ | ---------------------------------------------- |
| `String` | `next()`     | 从此扫描仪查找并返回下一个完整令牌。           |
| `String` | `nextLine()` | 使此扫描器前进==超过当前行==并返回跳过的输入。 |

 [Java 中 `next()` 和 `nextLine()` 方法的区别](https://www.delftstack.com/zh/howto/java/java-next-and-nextline/#java-中-next-和-nextline-方法的区别)

| `next()`                                 | `nextLine()`                                    |
| :--------------------------------------- | :---------------------------------------------- |
| 它从输入设备读取输入直到它到达字符空间。 | 它从输入的设备读取输入，直到线路改变。          |
| 它无法读取带有空格的单词。               | 它可以读取带有空格的单词。                      |
| 它在获得空间后停止读取输入。             | ==一旦获得`\n` 或按回车键，它将停止读取输入。== |
| 光标在接收到输入后放置在同一位置。       | ==光标将在读取输入后放置在下一行。==            |
| 转义 `next()` 的序列指的是空格。         | `nextLine()` 的转义序列是 `\n`。                |
| 扫描输入的语法：`Scanner.next()`         | 扫描输入的语法：`Scanner.nextLine()`            |



### **2. 输出**

1. System.out.println();//换行打印，输出之后会自动换行
2. System.out.print();//不换行打印
3. System.out.printf();//按格式输出

### **3. 字符串处理 String**

String 类用来存储字符串，可以用charAt方法来取出其中某一字节，计数从0开始：

```text
String a = "Hello"; // a.charAt(1) = 'e'
```

用substring方法可得到子串，如上例

```text
System.out.println(a.substring(0, 4)) // output "Hell"
```

注意第2个参数位置上的字符不包括进来。这样做使得 s.substring(a, b) 总是有 b-a个字符。

字符串连接可以直接用 + 号，如

```text
String a = "Hello";
String b = "world";
System.out.println(a + ", " + b + "!"); // output "Hello, world!"
```

如想直接将字符串中的某字节改变，可以使用另外的StringBuffer类。

### **4. 高精度**

BigInteger和BigDecimal可以说是acmer选择java的首要原因。
函数：add, subtract, divide, mod, compareTo等，其中加减乘除模都要求是BigInteger(BigDecimal)和BigInteger(BigDecimal)之间的运算，所以需要把int(double)类型转换为BigInteger(BigDecimal)，用函数BigInteger.valueOf().

### **5. 进制转换**

String st = Integer.toString(num, base); // 把num当做10进制的数转成base进制的st(base <= 35).
int num = Integer.parseInt(st, base); // 把st当做base进制，转成10进制的int(parseInt有两个参数,第一个为要转的字符串,第二个为说明是什么进制). 
BigInter m = new BigInteger(st, base); // st是字符串，base是st的进制.

### 6. 数组排序

函数：Arrays.sort();

## 



### **1、多行输入**

以牛客上的奖学金一题为例，详细见下面代码：

```java
package learnACM;

import java.util.Arrays;
import java.util.Scanner;
// 题目
    // 小v今年有n门课，每门都有考试，为了拿到奖学金，小v必须让自己的平均成绩至少为avg。
    // 每门课由平时成绩和考试成绩组成，满分为r。
    // 现在他知道每门课的平时成绩为ai ,若想让这门课的考试成绩多拿一分的话，小v要花bi 的时间复习，不复习的话当然就是0分。
    // 同时我们显然可以发现复习得再多也不会拿到超过满分的分数。为了拿到奖学金，小v至少要花多少时间复习。

 // 输入描述:
        // 第一行三个整数n,r,avg(n大于等于1小于等于1e5，r大于等于1小于等于1e9,avg大于等于1小于等于1e6)，
        // 接下来n行，每行两个整数ai和bi，均小于等于1e6大于等于1
        // 示例1
        // 输入
        // 5 10 9
        // 0 5
        // 9 1
        // 8 1
        // 0 1
        // 9 100
        //Scanner类默认的分隔符就是空格
public class MultilineInput {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        while(sc.hasNext()){
            int n=sc.nextInt();
            int full=sc.nextInt();
            int avg=sc.nextInt();
            int[][] nums=new int[n][2];
            for(int i=0;i<n;i++){
                nums[i][0]=sc.nextInt();
                nums[i][1]=sc.nextInt();
            }
            //假定不会出现拿不到奖学金的情况
            if (n==1){
                System.out.println((avg-nums[0][0])*nums[0][1]);
                continue;
            }
            Arrays.sort(nums, (o1, o2) -> o1[1] - o2[1]);//按复习代价从小到大排序
            long sum=0;
            for(int[] a:nums) {
                sum+=a[0];
            }
            long limit=avg*n;
            int index=0;
            long time=0;
            while(sum<limit){
                int tmp=full-nums[index][0];
                //如果一门课程复习到满分，小于限制
                if(tmp+sum<=limit){                
                    time+=tmp*nums[index][1];
                    sum+=tmp;
                    index++;
                }
                //如果一门课程复习到满分，大于限制
                else{
                    time+=(limit-sum)*nums[index][1];
                    sum=limit;
                }
            }
            // 输出描述:
            // 一行输出答案。
            // 输出
            // 43
            System.out.println(time);
        }
    }
}
```

### **2、数组输入（分隔符为空格）**

本题以牛客上的路灯一题为例，输入为数组主要采取还循环条件，代码如下：

```java
package learnACM;

import java.util.Arrays;
import java.util.Scanner;

public class ArrayInput {
    // 题目描述
    // 一条长l的笔直的街道上有n个路灯，若这条街的起点为0，终点为l，第i个路灯坐标为ai ，
    // 每盏灯可以覆盖到的最远距离为d，为了照明需求，所有灯的灯光必须覆盖整条街，
    // 但是为了省电，要使这个d最小，请找到这个最小的d。
      // 输入描述:
        // 每组数据第一行两个整数n和l（n大于0小于等于1000，l小于等于1000000000大于0）。
        // 第二行有n个整数(均大于等于0小于等于l)，为每盏灯的坐标，多个路灯可以在同一点。
        // 输入
        // 7 15
        // 15 5 3 7 9 14 0
    public static void main(String[] args){
        Scanner sc=new Scanner(System.in);
        while(sc.hasNext()){
            int n=sc.nextInt();
            long l=sc.nextLong();
            long[] nums=new long[n];
            for(int i=0;i<n;i++){
                nums[i]=sc.nextLong();
            }
            Arrays.sort(nums);
            long gap=nums[1]-nums[0];
            for(int i=1;i<n;i++){
                gap=Math.max(gap,nums[i]-nums[i-1]);
            }
            //下标最小和最大位置的路灯需要单独判断
            //如下标为3是最小，那么0-3这一段必须被覆盖到，所以最小下标必须单独判断
            gap=Math.max(gap,nums[0]*2);
            gap=Math.max(gap,(l-nums[n-1])*2);
            // 输出描述:
            // 输出答案，保留两位小数。
            // 输出
            // 2.50
            System.out.println(String.format("%.2f",gap/2.0));
        }
    }
}
```

### **3、输入为一个链表**

这里选用最经典的反转链表题目作为例子。

```java
package learnACM;
import java.util.Scanner;
import java.util.Stack;
    //题目描述
    //对于一个链表 L: L0→L1→…→Ln-1→Ln,
    //将其翻转成 L0→Ln→L1→Ln-1→L2→Ln-2→…

    //先构建一个节点类，用于链表构建
public class LinkListInput {
    static class LinkNode {
        int val;
        LinkNode next;
        public LinkNode(int val){
            this.val = val;
        }
    }
		//输入是一串数字，请将其转换成单链表格式之后，再进行操作
        //输入描述:
        //一串数字，用逗号分隔
        //输入
        //1,2,3,4,5
    public static void main(String[] args){
       
        Scanner scanner = new Scanner(System.in);
        //以字符串形式作为输入
        String str = scanner.next().toString();
        //通过分隔符将其转为字符串数组
        String[] arr  = str.split(",");
        //初始化一个整数数组
        int[] ints = new int[arr.length];
        //给整数数组赋值
        for(int j = 0; j<ints.length;j++) {
            ints[j] = Integer.parseInt(arr[j]);
        }
        Stack<LinkNode> stack = new Stack<>();
        LinkNode head = new LinkNode(0);
        LinkNode p = head;
        //链表初始化并放入stack中
        for(int i = 0; i < ints.length; i++){
            p.next = new LinkNode(ints[i]);
            p = p.next;
            stack.add(p);
        }
        head = head.next;
        //开始链表转换
        p = head;
        LinkNode q = stack.peek();
        while ((!p.equals(q)) && (!p.next.equals(q))) {
            q = stack.pop();
            q.next = p.next;
            p.next = q;
            p = p.next.next;
            q = stack.peek();
        }
        q.next = null;
        //输出
        //1,5,2,4,3
        //打印
        while (head != null) {
            if(head.next == null){
                System.out.print(head.val);
            }else{
                System.out.print(head.val + ",");
            }
            head = head.next;
        }
    }
}
```

### **4、树的输入（主要是构建树的过程）**

构建树的过程因题目而异，但是大体的思路可以参考以下代码

```java
package learnACM;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Stack;

//题目描述
//给定一个二叉树，判断其是否是一个有效的二叉搜索树。
//假设一个二叉搜索树具有如下特征：
//节点的左子树只包含小于当前节点的数。
//节点的右子树只包含大于当前节点的数。
//所有左子树和右子树自身必须也是二叉搜索树。
//例如：
//输入：
//    5
//   / \
//  1   3
//     / \
//    4   6
//输出: false

//构造树需要的结点类
class TreeNode {
    TreeNode left, right;
    int val;

    public TreeNode(int val) {
        this.val = val;
    }
}
 //输入描述:
        //第一行两个数n,root，分别表示二叉树有n个节点，第root个节点时二叉树的根
        //接下来共n行，第i行三个数val_i,left_i,right_i，
        //分别表示第i个节点的值val是val_i,左儿子left是第left_i个节点，右儿子right是第right_i个节点。
        //节点0表示空。
        //1<=n<=100000,保证是合法的二叉树
        //输入
        //5 1
        //5 2 3
        //1 0 0
        //3 4 5
        //4 0 0
        //6 0 0
public class TreeInput {
    public static void main(String[] args) throws IOException {
       
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        String[] s = reader.readLine().split(" ");
        int n = Integer.parseInt(s[0]);
        int root = Integer.parseInt(s[1]);
        TreeNode[] tree = new TreeNode[n + 1];
        int[][] leaf = new int[n + 1][2];
        for (int i = 1; i <= n; i++) {
            String[] ss = reader.readLine().split(" ");
            int val_i = Integer.parseInt(ss[0]);
            int left_i = Integer.parseInt(ss[1]);
            int right_i = Integer.parseInt(ss[2]);
            TreeNode node = new TreeNode(val_i);
            leaf[i][0] = left_i;
            leaf[i][1] = right_i;
            tree[i] = node;
        }
        for (int i = 1; i <= n; i++) {
            int left = leaf[i][0];
            if (left != 0) {
                tree[i].left = tree[left];
            } else {
                tree[i].left = null;
            }
            int right = leaf[i][1];
            if (right != 0) {
                tree[i].right = tree[right];
            } else {
                tree[i].right = null;
            }
        }
        TreeNode head = tree[root];
        boolean flag = isBinarySearchTree(head);
        System.out.println(flag);

    }

    private static boolean isBinarySearchTree(TreeNode node) {
        if(node == null){
            return true;
        }
        int pre = Integer.MIN_VALUE;
        Stack<TreeNode> s = new Stack<>();

        while(!s.isEmpty() || node != null){
            while(node != null){
                s.push(node);
                node = node.left;
            }
            node = s.pop();
            if(node == null){
                break;
            }
            if(pre > node.val){
                return false;
            }
            pre = node.val;
            node = node.right;
        }
        return true;
    }
}
```

## 三、编程题

### **1、矩阵元素相乘**

A[n,m]是一个n行m列的矩阵，a[i,j]表示A的第i行j列的元素，定义x[i,j]为A的第i行和第j列除了a[i,j]之外所有元素(共n+m-2个)的乘积，即x[i,j]=a[i,1]*a[i,2]*...*a[i,j-1]*...*a[i,m]*a[1,j]*a[2,j]...*a[i-1,j]*a[i+1,j]...*a[n,j],现输入非负整形的矩阵A[n,m]，求MAX(x[i,j])，即所有的x[i,j]中的最大值。

**输入描述:**

```text
第一行两个整数n和m。之后n行输入矩阵，均为非负整数。
```

**输出描述:**

```text
一行输出答案。
```

示例1

输入

```text
3 5
5 1 8 5 2
1 3 10 3 3
7 8 5 5 16
```

输出

```text
358400
```

Java

```text
import java.util.Scanner;
public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        while(sc.hasNext()){
            int n = sc.nextInt();
            int m = sc.nextInt();
            int[][] a = new int[n][m];
            for(int i=0;i<n;i++){
                for(int j=0;j<m;j++){
                    a[i][j] = sc.nextInt();
                }
            }
            int max=0;
            for(int i=0;i<n;i++){
                for(int j=0;j<m;j++){
                  int res=1;
                    for(int k=0;k<m;k++){
                        if(k!=j){
                            res*=a[i][k];
                        } 
                    }
                    for(int k=0;k<n;k++){
                        if(k!=i){
                            res*=a[k][j];
                        }
                    }
                    if(max<res){
                        max=res;
                    }
                }
            } 
            System.out.println(max);  
        }
    }
}
```

Python

```java
while True:
    try:
        n,m = map(int,input().split())
    except:
       break
    a = []
    for i in range(n):
        b = list(map(int,input().split()))
        a.append(b)   
    ma = 0
    for i in range(n):
        for j in range(m):
            res=1
            for k in range(m):
                if k!=j:
                    res*=a[i][k]
            for k in range(n):
                if k!=i:
                    res*=a[k][j]
            if ma<res:
                ma=res                
    print(ma)
```

### **2、有序数组去重**

给定一个字符串，字符串是有序的整数集合，逗号相连，移除相同的数字，使每个数字只出现一次，输出最终的数字个数。

**输入描述:**

```text
1,2,2
```

**输出描述:**

```text
2
```

示例1

输入

```text
1,2,2
```

输出

```text
2
```

示例2

输入

```text
0,0,1,1,1,2,2,3,3,4
```

输出

```text
5
```

**备注:**

有序整数字符串集合请在控制台一行内完成输入，并用英文逗号(,)相隔，如：1,2,2

Java

```java
import java.util.Scanner;
public class Main{
    public static void main(String arg[]){
        Scanner sc = new Scanner(System.in);
        String[] str=sc.nextLine().split(","); 
        int count = 0;
        for (int i = 0; i < str.length-1; i++) {
            if (str[i].equals(str[i+1])){
                count++;
            }
        }
        System.out.println(str.length-count);
    }
}
```

Python

```text
s=input().split(',')
s=set(s)
print(len(s))
```

### **3、最大子序列和**

给一个长度为N的序列a1,a2,...,an,求最大连续和。也即，寻找1<=i<=j<=N,使得ai+...+aj尽量大。

**输入描述:**

```text
一行, 整数序列, 逗号分隔
```

**输出描述:**

```text
一行, 整数, 表示最大子序列和
```

示例1

输入

```text
1, 2, -5, 3, 4
```

输出

```text
7
```

Java

```java
import java.util.Scanner;
public class Main{
    public static void main(String arg[]){
        Scanner sc = new Scanner (System.in);
        String[] str=sc.nextLine().replace(" ","").split(",");
        int[] a = new int[str.length];
        int k = 0;
        for (String temp : str) {
            a[k++] = Integer.parseInt(String.valueOf(temp));
        }
        if(a.length==1){
            System.out.print(a[0]);
        }else{
          int temp=0,ma=a[0];
            for(int i:a){
                temp=Math.max(temp+i,i);
                ma=Math.max(ma,temp);
            }
            System.out.print(ma);
        }
    }
}
```

Python

```text
A=list(map(int,input().strip().split(',')))
temp=0
ma=A[0]
for a in A:
    temp=max(a+temp,a)
    ma=max(temp,ma)
print(ma)
```

### **4、回文串**

回文串是指字符串无论从左读还是从右读，所读的顺序是一样的；简而言之，回文串是左右对称的。

现给定一个字符串，求出它的最长回文子串。你可以假定只有一个满足条件的最长回文串。

**输入描述:**

```text
一行, 字符串
```

**输出描述:**

```text
一行, 字符串
```

示例1

输入

```text
yabccbau
```

输出

```text
abccba
```

Python

```text
st=input()
a=''
for i in range(len(st)):
    for j in range(i+1,len(st)+1):
        s=st[i:j]
        if(s==s[::-1]):
            if(len(a)<len(s)):
                a=s
print(a)
```

### **5、变形词**

对于两个字符串A和B，如果A和B中出现的字符种类相同且每种字符出现的次数相同，则A和B互为变形词，请设计一个高效算法，检查两给定串是否互为变形词。

给定两个字符串A和B，请返回一个bool值，代表他们是否互为变形词。

**输入描述:**

```text
两行，每行各一个字符串s，s长度小于1000
```

**输出描述:**

```text
bool 值
```

示例1

输入

```text
bcbc
cbcb
```

输出

```text
1
```

Python

```text
s1=input()
s2=input()
st1=[]
st2=[]
if len(s1)!=len(s2):
    print(0)
else:
    for i in range(len(s1)):
        if s1[i] not in st1:
            st1.append(s1[i])
    for j in range(len(s2)):
        if s2[j] not in st2:
            st2.append(s2[j])
    flag=0
    for k in range(len(st1)):
        if s1.count(st1[k])!=s2.count(st1[k]):
            flag=1
            print(0)
            break
    if(flag==0):
        print(1) 
```

### **6、连续质数表示**

一些正数能被表示成一个或者多个连续质数的和。那一个数会有多少种这样的表示方式呢？比如说数字41能有3种表示方式：2+3+5+7+11+13，11+13+17，和41；数字3只有本身这一种表示方式；而20没有这样的表示方式。写一个程序生成给定数字的表示方式数量吧。数字大小范围从2到10，000。 

**输入描述:**

```text
一行，包含一个2到10000的正整数
```

**输出描述:**

```text
一行, 非负整数, 给定数字的表示方式数量
```

示例1

输入

```text
41
```

输出

```text
3
```



## 360

<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220827155907392.png" alt="image-20220827155907392" style="zoom:67%;" />

~~~java 
ATTTAA
TTAATT
    
ATTTAATT
TTAATTAA

样例输出
3
    
3 3 3
i you he
am is are
yours his hers
5
i am yours
you is his
he are hers yours
i am am yours
is his



YES
YES
YES
NO
NO
~~~

<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220827155925356.png" alt="image-20220827155925356" style="zoom:67%;" />

## 京东

<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220827205733452.png" alt="image-20220827205733452" style="zoom:50%;" />

```
6
1 1 4 5 1 4

3

5
2 1 3 2 4

[2 1 2 1 2]
3

```





<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220827205802806.png" alt="image-20220827205802806" style="zoom:50%;" />

## 顺丰

![image-20220831182936897](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220831182936897.png)



```
样例输入
5
样例输出
11
```



![image-20220831183024913](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220831183024913.png)

```
样例输入
3
1 1
1 -1 1
样例输出
3
提示
首先选择1、2节点构成的子树+1，然后选择1、3节点构成的子树-1，最后选择1节点构成的子树-1
```



~~~
SWORDMAN
3


K1 Q7

A1 A8
~~~



<img src="C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220903115752611.png" alt="image-20220903115752611" style="zoom:50%;" />

~~~
6
1 2 2 1 4
ABCCAD

~~~





## 去哪儿

![image-20220907211348989](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220907211348989.png)

![image-20220907211408203](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20220907211408203.png)





```
3 2
xinguan feiyan xinzeng bendi quezhen anli
ju baodao chengdu xinzeng xinguan feiyan bendi quezhen anli yili shenzhen xinzeng bendi quezhen anli liangli yiqing zhengti kongzhi lianghao
xinguan yimiao linchuang shiyan
wuzhong xinguan yimiao tongguo sanqi linchaung shiyan xiaoguo lianghao


xinguan xinzeng bendi

新冠肺炎新增本地确诊案例

据报道成都新增新冠肺炎本地确诊案例一例，深圳新增案例两例，疫情整体控制良好，本地确诊案例两例，疫情整体控制良好。

新冠疫苗临床试验

五种新冠疫苗通过三期临床试验，效果良好。

1 2
xinguan feiyan xinzeng bendi quezhen anli
jubaodao chengdu xinzeng xinguan feiyan bendi quezhen anli yili shenzhen xinzeng bendi quezhen anli liangli yiqing zhengti kongzhi lianghao
xinguan yimiao linchuang shiyan
wuzhong xinguan yimiao tongguo sanqi linchaung shiyan xiaoguo lianghao

xinguan
```





```none
4
0,2,200,0,1
1,3,400,0,1
2,3,400,1,0
3,3,300,0,1
3 1 3 200 0 1


6
0,2,200,0,1
1,4,330,2,1
2,3,400,3,1
3,3,310,1,1
4,3,320,8,1
5,3,330,0,1
3 2 3 300 9 2

4
5 2 6 1


5
2 3 1 1 4
1
```
