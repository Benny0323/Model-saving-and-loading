# Model-saving-and-loading

pytorch保存模型非常简单，主要有两种方法：

只保存参数；（官方推荐）

保存整个模型 (结构+参数)。

torch.save( )实现对网络结构和模型参数的保存。有两种保存方式：
**一是保存整个神经网络的的结构信息和模型参数信息，save的对象是网络模型；**

**二是只保存神经网络的训练模型参数，save的对象是net.state_dict( )**。

假设我有一个训练好的模型名叫net1,则

torch.save(net1, ‘7-net.pth’) # 保存整个神经网络的结构和模型参数

torch.save(net1, ‘7-net.pkl’)  # 同上

torch.save(net1.state_dict(), ‘7-net_params.pth’) # 只保存神经网络的模型参数

torch.save(net1.state_dict(), ‘7-net_params.pkl’)  # 同上

如果你是使用torch.save方法来进行模型参数的保存，那保存文件的后缀其实没有任何影响，结果都是一样的，很多.pkl的文件也是用torch.save保存下来的，和.pth文件一模一样的。不管pkl文件还是pth文件，都是以二进制形式存储的，没有本质上的区别，你用pickle这个库去加载pkl文件或pth文件，效果都是一样的。

由于保存整个模型将耗费大量的存储，故官方推荐**只保存参数**，然后在建好模型的基础上加载。

一、只保存模型参数
