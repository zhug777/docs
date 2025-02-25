## [torch 参数更多 ]torch.range

### [torch.range](https://pytorch.org/docs/stable/generated/torch.arange.html?highlight=arange#torch.range)
```python
torch.range(start=0,
            end,
            step=1,
            *,
            out=None,
            dtype=None,
            layout=torch.strided,
            device=None,
            requires_grad=False)
```
### [paddle.arange](https://www.paddlepaddle.org.cn/documentation/docs/zh/api/paddle/arange_cn.html#arange)
```python
paddle.arange(start=0,
              end=None,
              step=1,
              dtype=None,
              name=None)
```

其中 Pytorch 相比 Paddle 支持更多其他参数，具体如下：
### 参数映射
| PyTorch       | PaddlePaddle | 备注                                                   |
| ------------- | ------------ | ------------------------------------------------------ |
| start  |  start  | 表示起始位置。 |
| end | end  | 表示结束位置。   |
| step | step  | 表示步长。   |
| <font color='red'> out </font> | -  | 表示输出的 Tensor ， Paddle 无此参数，需要进行转写。    |
| dtype        | dtype           | 表示数据类型。                   |
| <font color='red'> layout </font> | -       | 表示布局方式， Paddle 无此参数，一般对网络训练结果影响不大，可直接删除。  |
| <font color='red'> device </font>     | -       | 表示 Tensor 存放设备位置，Paddle 无此参数，需要进行转写。 |
| <font color='red'> requires_grad </font> | -       | 表示是否计算梯度， Paddle 无此参数，需要进行转写。 |


### 转写示例

#### out：指定输出
```python
# Pytorch 写法
torch.range(5, out=y)

# Paddle 写法
paddle.assign(paddle.arange(5), y)
```

#### device: Tensor 的设备
```python
# Pytorch 写法
torch.range(5, device=torch.device('cpu'))

# Paddle 写法
y = paddle.arange(5)
y.cpu()
```

#### requires_grad：是否需要求反向梯度，需要修改该 Tensor 的 stop_gradient 属性
```python
# Pytorch 写法
x = torch.range(5, requires_grad=True)

# Paddle 写法
x = paddle.arange(5)
x.stop_gradient = False
```
