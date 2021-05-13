# Check List

#### Check List

**测试而不是评估**

如何评估nlp模型呢？accuracy？在held-out dataset上的正确率往往是偏高的，生产环境中完全是另一番光景。perplexity？只能用于衡量Language model，详细可以看之前的bolg。近些年也有不少方法，可惜只能用于特定的任务或问题。

那么现在我们转变一下思路，不再**评估**nlp模型，而是**测试**模型。这个思路启发自软件工程。在软件工程有一套完整的测试系统，判断代码是否可靠，定位故障出在那里，找到瓶颈所在。我们是否可以用单元测试、黑盒测试等，类似的方式来测试nlp模型呢。

**Behavioral Testing**

behavioral testing，也就是所谓的black-box testing。

```text
 def add(a, b):
     return a + b
 ​
 def test_add():
     assert add(1, 2) == 3
     assert add(1, 0) == 1
     assert add(-1, 1) == 0
     assert add(-1, -1) == -2
```

nlp模型应该有哪些behavioral呢，我们希望我们的nlp模型是真的可以理解人类的语言，而不是只靠一些关键字什么的“走捷径”。

那么，我们希望nlp模型可以理解句子的成分，知道句子里的哪些内容无关紧要，知道不同的说法其实是一个意思等等等等。我不管你是怎么做到的，不管attention或者神经网络得到了怎样的权重，不管语料是否存在什么问题，不管你是用了惊为天人的技巧还是老老实实梯度下降。只要你（nlp模型）具备上述提到的功能（behavioral），那就是个好模型。

那么，为了检验你是否具备这些功能，我们需要一些测试用例。

**测试用例**

原论文以情感分析（积极or消极）为例提供了很多样例  


