## 链表中的节点每k个一组翻转

### 描述
将给出的链表中的节点每 k 个一组翻转，返回翻转后的链表
如果链表中的节点数不是 k 的倍数，将最后剩下的节点保持原样
你不能更改节点中的值，只能更改节点本身。

例如：
给定的链表是 1\to2\to3\to4\to51→2→3→4→5
对于 k = 2k=2 , 你应该返回 2\to 1\to 4\to 3\to 52→1→4→3→5
对于 k = 3k=3 , 你应该返回 3\to2 \to1 \to 4\to 53→2→1→4→5


### 示例
输入：
{1,2,3,4,5},2
返回值：
{2,1,4,3,5}

### 思路

- 递归

### 解决
```javascript
function ListNode(x){
   this.val = x;
   this.next = null;
}
function reverseKGroup(head, k) {
  // write code here
  let pre = null;
  let current = head;
  let node = head;
  for (let i = 0; i < k; i++) {
    if (node === null) {
      return head;
    }
    node = node.next;
  }
  for (let i = 0; i < k; i++) {
    let t = current.next;
    current.next = pre;
    pre = current;
    current = t;
  }
  head.next = reverseKGroup(current, k);
  return pre;
}
```

