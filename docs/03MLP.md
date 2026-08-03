# 本节内容
1. 课程引入与问题背景
2. 电路启发：组合解决异或
3. 多层感知机原理与结构
4. 非线性激活的必要性
5. 训练难题与反向传播

# 电路启发

## 逻辑电路异或门
> [!TIP]  
> **由简单模块组合复杂功能**

XOR 问题早在逻辑电路得到解决，计算机的异或门是由更基础的门电路组合而成的

```mermaid
graph LR
	%% 定义节点及形状
	x1((x1))
	x2((x2))
	or[OR]
	nand[NAND]
	and[AND]
	out["Y = x1 ⊕ x2<br>(XOR)"]

	%% 第一步：输入层
	subgraph Step1["第一步：输入层"]
		direction LR
		x1
		x2
	end
	
	%% 第二步：隐藏层
	subgraph Step2["第二步：隐藏层"]
		direction TB
		or
		nand
	end
	
	%% 第三步：输出层
	subgraph Step3["第三步：输出层"]
		direction TB
		and
		out
	end

	%% 定义连接线
	x1 -->  or
	x1 --> nand
	x2 --> or
	x2 --> nand
	or --> and
	nand --> and
	and --> out

	%% 样式设置（背景色和虚线边框）
	style Step1 fill:#f4f9fd,stroke:#85c1e9,stroke-dasharray: 5 5,color:#1a5276
	style Step2 fill:#f4fbf5,stroke:#82e0aa,stroke-dasharray: 5 5,color:#145a32
	style Step3 fill:#fdf6f0,stroke:#f5b041,stroke-dasharray: 5 5,color:#935e38
	
	classDef default fill:#fff,stroke:#333,stroke-width:2px;
```

- $\text{OR} \to x_1 \ \text{OR} \ x_2$ : 至少一个输入为 1
- $\text{NAND not and} \to \text{NOT}(x_1 \ \text{AND} \ x_2)$ : 两个输入不同时为 1

## 两层感知机解决XOR

> [!TIP]  
> 两层感知机通过组合简单的线性分隔（OR 和 NAND），在最后一层实现异或（XOR）


```mermaid
graph LR
	%% 定义节点样式
	classDef inputNode fill:#dae8fc,stroke:#6c8ebf,stroke-width:2px;
	classDef hiddenNode fill:#d5e8d4,stroke:#82b366,stroke-width:2px;
	classDef outputNode fill:#ffe6cc,stroke:#d79b00,stroke-width:2px;
	classDef textNode fill:none,stroke:none;
	classDef tableNode fill:#fff,stroke:#d79b00,stroke-width:1px;

	subgraph Layer1 ["第 1 层：输入层"]
		direction TB
		x1((x<sub>1</sub>)):::inputNode
		x2((x<sub>2</sub>)):::inputNode
		InputLabel["输入： (x<sub>1</sub>, x<sub>2</sub>) ∈ {0, 1}<sup>2</sup>"]:::textNode
	end

	subgraph Layer2 ["第 2 层：隐藏层"]
		direction TB
		HiddenLabel["2 个神经元"]:::textNode
		h1((h<sub>1</sub>)):::hiddenNode
		h2((h<sub>2</sub>)):::hiddenNode
		HiddenCondition["h<sub>1</sub> = step( x<sub>1</sub> + x<sub>2</sub> - 0.5)<br>h<sub>2</sub> = step(-x<sub>1</sub> - x<sub>2</sub> + 1.5)<br>h<sub>1</sub> = 1 当且仅当 (x<sub>1</sub>, x<sub>2</sub>) ≠ (0,0)<br>h<sub>2</sub> = 1 当且仅当 (x<sub>1</sub>, x<sub>2</sub>) ≠ (1,1)"]:::textNode
	end

	subgraph Layer3 ["第 3 层：输出层"]
		direction TB
		OutputLabel["1 个神经元"]:::textNode
		y((<b>y</b>)):::outputNode
	end

	%% 连接线（包含权重）
	x1 --> |w<sub>11</sub> =1| h1
	x2 --> |w<sub>21</sub> =1| h1
	x1 --> |w<sub>12</sub> =-1| h2
	x2 --> |w<sub>22</sub> =-1| h2
	h1 --> |v<sub>1</sub> =1| y
	h2 --> |v<sub>2</sub> =1| y

%% 设置虚线区域样式
style Layer1 fill:#f4f9fd,stroke:#8cb9e8,stroke-width:2px,stroke-dasharray: 5 5,color:#1a5276
style Layer2 fill:#f4fbf5,stroke:#82e0aa,stroke-width:2px,stroke-dasharray: 5 5,color:#145a32
style Layer3 fill:#fdf6f0,stroke:#f5b041,stroke-width:2px,stroke-dasharray: 5 5,color:#935e38

%% 为了保证同层文本节点能排布在圆点周围，可以改变连接方向的顺序，或者利用 Mermaid 的布局自然浮动
```

- 输入层  
	接收两个特征 $x_1 \ , \ x_2$
- 隐藏藏  
	两个神经元使用不同的权重并行运算，各自画一条分割线，输出 0 或 1
- 输出层  
	将隐藏层的两个输出作为输入，再一次加权求和后激活，得到异或判断

| $x_1$ | $x_2$ | y(XOR) |
|:-----:|:-----:|:------:|
|0|0|0|
|0|1|1|
|1|0|1|
|1|1|0|

第一个隐藏层学会 **至少一个输出为 1**  
第二个隐藏层学会 **输出不能同时为 1**  
输出层对两个条件取交集  

# 多层感知机的原理与结构

## 多层结构的思想来源
1. 神经科学  
	大脑皮层是分层处理的  
	底层神经元响应边缘和方向，高层神经元响应人脸和物体  
2. 函数逼近理论  
	任何函数都可以用简单函数的组合来逼近  
	泰勒展开、傅里叶变换等  

## 多层感知机的一般结构
多个感知机按层排列，层间全连接，构成了 **多层感知机 (MLP)**
- 输入层接收原始特征，数个隐藏层进行中间预算，输出层给出最终结果
- 同一层的神经元 **并行提取多个不同的特征或规则**
- 后续层将前一层的输出作为输入，利用不同权重进一步组合，**逐层构造更加抽象、更加有效的表达**

数学表达：**函数的层层嵌套**
$$output = h_n(h_{n-1}(\ldots(h_2(h_1(X)))))$$

# 非线性激活的必要性

## 为何多层线性变换无效
假设  
第一层输出为 $h = W_1 x + b_1$   
第二层输出为 $y = W_2 h + b_2$   
即 $y = W_2(W_1x+b_1)+b_2 = (W_2 W_1)x + (W_2b_1 + b_2)$   
令 $W' = W_2W_1, \ b' = W_2b_1 +b_2$  
则 $y = W'x + b'$ , 仍为线性形式

> [!TIP]  
> 线性变换的组合仍是线性变换  
> 即便层层叠加也是徒劳  

## 使用激活函数打破线性
在每个神经元的加权求和输出上加一个非线性函数，称为 **激活函数 (Activation Function)**  
$$ h = f(Wx + b)$$

引入非线性的 $f$ , 层间组合无法被化简为单一线性变换  

**阶跃函数 (Step Function)**

$$
step(z) = 
\begin{cases}
	1 \ 若 \quad z \ge 0\\
	0 \ 若 \quad z < 0\\
\end{cases}
$$

## 万能逼近定理
1989 年正式证明了 **万能逼近定理 (Universal Approximation Theorem)**

> [!Note]万能逼近定理  
> 一个含有充足神经元的单隐藏层 MLP, 可以任意精度逼近任意连续函数

- 意味 MLP 在理论上具备表达任何函数的能力  
- **表达能力** (足够多神经元) 和 **训练能力** (如何找到正确权重) 是两个不同问题  

深度学习而非宽度学习  
后续训练发现增加隐藏层的层数，比增加层内的神经元数量，能取得更佳的效果  

# 训练难题与反向传播

## 模型训练仍是难题
多层网络能力如此强大，为何深度学习还会经历二十多年寒冬？  
- MLP 结构早在 1960 年代提出，虽然有人想到多层网络，但是 **没法训练**  
- 当时的感知机学习规则 **只适用于单层网络**  
- **核心难题是如何分配隐藏层误差**  
	1. 如何分配层间误差，确定哪个隐藏层的误差
	2. 如何分配层内误差，确定哪个神经元权重的误差

1986 年，**反向传播算法 (Back propagation)** 与多层网络结合，形成高效计算多层梯度方法  

