# BoWen_Patents

博文参与的成果计划

1. ring_allreduce 进阶
1.1 ring_allreduce + transformer(K,Q,V)，动机：提高 transformer 反向 Q，K，V 三个张量的同步（all_reduce）的速度。
1.2 ring_allreduce（提升规约精度） + PipeDream（memory_placement节省内存开销、加快 fw & bw 计算，提升整网收敛速度）。

2. routing_op 路由算子
对于分布在不同 Device 上的 op 或子图，这些跨 Device 的 op/子图之间生产和消费 tensor，为满足该 tensor 特定的分布式 Placement 需求，需要插入 routing_op 路由算子改变
该 tensor 的 Device Placement 属性。这里归纳和抽象出统一的 routing_op 路由算子。

可组成 routing_op 路由算子的集中可选通信原语算子：
1. 聚合
1.2 reduce、all_reduce、ring_allreduce (=scatter_reduce + all_gather)
1.3 gather、all_gather

3. 分发
3.1 broadcast
3.2 scatter、scatter_reduce
