第一、[PipeDream 这个思想已被 Facebook 团队的 PorTorch 框架用在计算图 fw+bw 同步中](https://pytorch.org/docs/stable/pipeline.html)<br>


第二、[PipeDream 被微软用在框架计算图分布式情形下 Device Placement](https://papers.nips.cc/paper/2020/file/b14680dec683e744ada1f2fe08614086-Paper.pdf)<br>
[Device Placement 代码](https://github.com/msr-fiddle/dnn-partitioning#:~:text=Efficient%20Algorithms%20for%20Device%20Placement%20of%20DNN%20Graph,3%20Latency%20minimization.%20...%204%20Legal%20notices.%20)

第三、[Device Placement 正在被我们用在 Memory/Register Placement 中解决分布式流水系统中，节省内存开销、加快 fw+bw 过程的 1f1b 的流水并行系统](https://BoWen)<br>

PyTorch 的 PipeDream <br>
https://pytorch.org/docs/stable/pipeline.html

![image](https://user-images.githubusercontent.com/31394900/159654792-5afc9548-4c54-4cd3-a3ad-a70941f4354a.png)

![image](https://user-images.githubusercontent.com/31394900/159654841-25db0aad-8575-451f-898f-d2e835b4272a.png)


![B2233226-FED2-43f1-A002-8DAA11E40745](https://user-images.githubusercontent.com/31394900/159637326-d8fb6ec1-8b28-4008-9ddd-cee574def088.png)

数据流过整个计算图（fw+bw）时自动流水分配内存的示意图<br>

纵轴方向：<br>
-计算图流 (fw+bw)   红-> 黄 -> 绿 -> 灰<br>

横轴方向：<br>
-数据流     1-> 2-> 3-> 4 <br>

batch = 5 第五批次数据进入系统的时间点：第 1 批数据流过反向计算图。batch = 1 的反向结束。开始加载第5批次数据。<br>

<img width="727" alt="image" src="https://user-images.githubusercontent.com/31394900/159651832-9bfa37ce-0886-4a68-a055-d4c0b213a180.png">


![image](https://user-images.githubusercontent.com/31394900/159724663-be7382b5-a2a5-457d-8400-63dbae09bfdb.png)


上图论文实现的是 device placement (device 放置)<br>
博文现在写的是 register/memory palcement.<br>

两者共同点都是解决计算图fw+bw 过程 Tensor 生产和消费过程分布式放置的流水系统。<br>
