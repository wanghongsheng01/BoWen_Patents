PyTorch 的 PipeDream <br>
https://pytorch.org/docs/stable/pipeline.html

![image](https://user-images.githubusercontent.com/31394900/159654792-5afc9548-4c54-4cd3-a3ad-a70941f4354a.png)

![image](https://user-images.githubusercontent.com/31394900/159654841-25db0aad-8575-451f-898f-d2e835b4272a.png)


![B2233226-FED2-43f1-A002-8DAA11E40745](https://user-images.githubusercontent.com/31394900/159637326-d8fb6ec1-8b28-4008-9ddd-cee574def088.png)

数据流过整个计算图（fw+bw）时自动流水分配内存的示意图

纵轴方向：
-计算图流 (fw+bw)   红-> 黄 -> 绿 -> 灰

横轴方向：
-数据流     1-> 2-> 3-> 4 

batch = 5 第五批次数据进入系统的时间点：第 1 批数据流过反向计算图。batch = 1 的反向结束。开始加载第5批次数据。

<img width="727" alt="image" src="https://user-images.githubusercontent.com/31394900/159651832-9bfa37ce-0886-4a68-a055-d4c0b213a180.png">

