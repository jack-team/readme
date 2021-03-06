###一. react 在没有对diff算法进行优化的时候，它的复杂度是o(n^3)，效率比较低,要比较一个1000个节点的组件，需要执行上亿次。
###二 . react 优化后的算法

1. 使用三种 策略优化了复杂度  (tree diff，component diff，element diff ) 复杂度变为o(n);
2. tree diff 对虚拟dom进行层级控制 只会比较同一父级下的节点，不会跨级比较，减少复杂度。如果出现跨层级的操作，
react直接删除再创建，所以性能不好，react官方不推荐跨层级节点操作;
3. component diff 如果是同一类型的组件的话，则会按照原有 虚拟dom算法进行比较，如果不是同一组件，则是直接删除。毕竟不同组件的dom相似度
不会很高
4. element diff

###三、总结：
1. React通过制定大胆的diff策略，将 O(n3) 复杂度的问题转换成 O(n) 复杂度的问题；
2. React是如何将O(n3) 复杂度的问题转换成 O(n) 的？
3. 只进行同级比较
4. 不同类的React组件会被当做完全不同的DOM结构而被完全替换
5. key prop：开发人员可以通过给Virtual DOM一个唯一的key属性暗示React这是同一个DOM结构，反之若key值不同则会被当做完全不同的DOM结构。
6. React通过分层求异的策略，对tree diff进行算法优化；
7. React通过相同类生成相似树形结构，不同类生成不同树形结构的策略，对component diff进行算法优化。
8. React通过设置唯一key的策略，对element diff进行算法优化；
9. 建议，在开发组件时，保持稳定的DOM结构会有助于性能的提升；
10. 建议，在开发过程中，尽量减少类似将最后一个节点移动到列表首部的操作，当节点数量过大或更新操作过于频繁时，在一定程度上会影响React的渲染性能。



