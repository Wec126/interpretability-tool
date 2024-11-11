# Captum中可用的Attribution Map算法

Captum更加关注于层 & neuron的贡献

Captum中包含的方法十分简单，并且关注到了模型本身、层和neuron

但是当中大部分方法针对于CNN

1. DeepLift & DeepLiftShap

   【黑盒】

   通过计算输入相对于某一基线的变化对输出的贡献，从而提供输入特征的重要性分数。

   SHAP：通过对多基线取平均的方式，模拟有可能的输入组合，从而更公平地分配每个特征的贡献

   由于涉及到反向传播，会十分耗时

   并且SHAP本身是特征组合的方式，会十分耗能

2. ==FeatureAblation==

   【黑盒】

   通过对输入特征消融来评估每个特征对模型预测的影响

3. ==FeaturePermutation==

   【黑盒】

   通过随机排列输入特征来评估每个特征对模型预测的影响

4. ==GradientShap==

   【黑盒】

   计算输出相对于输入特征的梯度，通过在基线值和原始输入之间进行插值，生成一系列扰扰动后的输入数据，对这些数据进行加权之后来近似Shapley值

   适用于较大模型

5. Deconvolution & GuidedBackpro

   通过反向传播技术，揭示输入图像中哪些区域对模型的输出有显著影响

   最初应用于CNN，在大型模型上存在一定问题

6. ==GuidedGradCam==

   【白盒】

   基于CAM，但是通过引入一个引导机制来提高可视化结果的准确性，这个引导机制一般是一个激活函数，用于增强重要的特征通道，同时抑制不重要的通道。

7. ==InputXGradint==

   【白盒】

   计算输入特征与对应梯度的乘机，来量化每个特征对模型预测的贡献

   只需要一次前向和一次反向传播

8. IntegratedGradients

   【白盒】

   使用积分方式，将模型的输入变化归因于输入特征的变化

   需要涉及到多次积分，不适用于较大模型

9. KernelShap

   【白盒】

   通过核函数来近似Shapley值，从而提供对模型决策过程的深入理解

   通过在基线输入和实际输入之间进行插值，生成一系列扰动后的输入数据

   计算量很大，需要生成多个扰动输入并进行多次预测；并且和函数的选择会直接影响到归因结果

10. LayerGradCam

    【白盒】

    允许用户选择不同的网络层来进行注意力映射

    由于需要计算相对于所选层的激活图的梯度，所以计算量较大

11. InternalInfluence

    【白盒】

    用于量化模型内部不同组件之间的相互影响

    计算量较大

12. LayerActivation

    【白盒】

    一种可视化工具

    通过观察模型在不同输入下的内部激活状态，去理解模型是如何处理和响应输入数据的

13. LayerConductance

    【白盒】

    基于Shapley理论，通过计算模型输出相对于特定层激活的归因来衡量该层对最终输出的影响

    不适用于大模型

14. LayerDeepLift & LayerDeepLiftShap

    更加关注于特定层的贡献

15. LayerFeatureAblation

16. LayerFeaturePermutation

17. LayerGradientShap

18. LayerGradientXActivation

19. LayerIntegratedGradients

20. LayerLRP

21. Lime,LimeBase

    【黑盒】

    旨在构建一个可解释性的模型来解释单个预测是如何做到的

    不适用于大模型！

22. LRP

23. NeuronConductance

24. NeuronDeepLift & NeuronDeepLiftShap

25. NeuronFeatureAblation

26. NeuronGradient

27. NeuronGradientShap

28. NeuronDeconvolution & NeuronGuidedBackprop

29. NeuronIntegratedGradients

30. ==NoiseTunnel==

    【黑盒】

    对输入添加噪声进而查看模型的结果，比较原始输入 & 噪声输入之间的差距来得到模型关注的部分

    涉及多次运行

31. ==Occlusion==

    【黑盒】

    通过遮挡输入数据中的不同区域

32. ==Saliency==

    【白盒】

    计算梯度，然后将梯度给特征生成热图进行可视化

    需要一次梯度计算

33. ShaplyValues & ShapleyValueSampling

    【黑盒】

    将模型的预测结果分解为各个特征的贡献之和，从而理解每个特征对最终预测的影响

    计算成本很高

## 2. 模型

| CV(基于transformer)                                          | 多模态                           | CV(不基于Transformer)不着急 |
| ------------------------------------------------------------ | -------------------------------- | --------------------------- |
| ViT(/data/wlc/models/vit)                                    | CLIP(/data/wlc/models/clip)      |                             |
| Siwn Transformer(/data/wlc/models/swin)                      | MMT                              |                             |
| Efficient Vision Transformers(/data/wlc/models/efficient-net) | siglip((/data/wlc/models/siglip) |                             |
| Deit(/data/wlc/models/deit)                                  |                                  |                             |





​    
