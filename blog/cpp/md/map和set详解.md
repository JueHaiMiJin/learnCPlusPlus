# map 和 set

map 和 set 都是 STL 中提供的关联式容器，其底层实现都是红黑树，由于 map 和 set 所开放的各种操作接口，红黑树也都实现了，所以几乎
所有的 map 和 set 操作行为，都只是间接调用红黑树的操作

### map 和 set 的区别

- map 中的元素是 key-value，关键字起到索引的作用，值则表示与索引相关联的数据，对于 set 而言，其则
是关键字的集合，set 中每个元素只包含一个关键字
- set 的迭代器是 const 的，不允许修改元素的值，map 允许修改 value，但不允许修改 key，其原因是 map 和 set 是根据
关键字排序来保证有序性的，如果允许修改 key 之后，那么首先需要删除该键，然后调节平衡，再插入修改后的键值，调节
平衡，如此一来严重破坏了 map 和 set 的结构，导致 iterator 失效，不知道应该指向改变前的位置还是改变后的位置，所以 STL 将
set 迭代器设置成 const，不允许修改迭代器的值，而 map 的迭代器则不允许修改 key 值，允许修改 value 值
- map支持下标操作，set不支持下标操作。map可以用key做下标，map的下标运算符[ ]将关键码作为下标去执行查找，如果关
键码不存在，则插入一个具有该关键码和mapped_type类型默认值的元素至map中，因此下标运算符[]在map应用
中需要慎用，const_map不能用，只希望确定某一个关键值是否存在而不希望
插入元素时也不应该使用，mapped_type类型没有默认值也不应该使用。如果find能解决需要，
尽可能用find。


