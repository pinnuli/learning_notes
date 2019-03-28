i. modCount 是 AbstractList 的属性值：`protected transient int modCount = 0;`
ii. modCount有什么用：这里需要先了解一下几个问题：
    - fail-fast 机制
fail-fast 机制是java集合(Collection)中的一种错误机制。当多个线程对同一个集合的内容进行操作时，就可能会产生fail-fast事件。例如：当某一个线程A通过iterator去遍历某集合的过程中，若该集合的内容被其他线程所改变了；那么线程A访问集合时，就会抛出ConcurrentModificationException异常，产生fail-fast事件。
    - 迭代器与ConcurrentModificationException
无论在直接迭代还是在Java5.0引入的for-each循环语法中，对容器类进行迭代的标准方式都是使用Iterator, 然而， 如果有其他线程并发地修改容器， 那么即使是使用迭代器也无法避免在迭代期间对容器加锁。在设计同步容器类的迭代器时并没有考虑到并发修改的问题， 并且它们表现出的行为是“ 及时失败" (fail-fast)的。这种“ 及时失败” 的迭代器井不是一种完备的处理机制，而只是“ 善意地” 捕获并发错误，因此只能作为并发问题的预警指示器。它们采用的实现方式是，将计数器的变化与容器关联起来： 如果在迭代期间计数器被修改， 那么hasNext或next将抛出ConcurrentModificationException。
     - 