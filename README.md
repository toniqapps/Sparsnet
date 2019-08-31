## Sparsenet

SparseNet is a variant of DenseNets or Resnet. In Densenet we have a skip connection after every block which are concatenated to next layer and in resnet we do cumulative summation, but both have same problems i.e. as the depth increases, the number of features grows linearly. Later features may corrupt or wash out the information carried by earlier features maps as seen in resnet which result in saturation of resnet performance, in contrast densnet preserves the original format of previous layers due to concatenation, this factor contribute to better parameter performance efficiency over resnet but due to concatenation no of parameters grows at the rate of  0(𝑁2)  due to which portion of network is devoted to process previously seen feature map and hence are not able to exploit all the parameters fully and this pitfall are due to the linear growth of feature maps in both densnet and resnet. To overcome this we would like to maintain the power of short gradient paths for training. By aggregating features only from layers with exponential offset the length of the shortest gradient path between blocks with offset S is bounded by  𝑂((𝑐−1)𝑙𝑜𝑔(𝑆)) . Here, c is again the base of the exponent governing the sparse connection pattern. The total number of output to the  𝑙𝑡ℎ  block is  𝑂(𝑙𝑜𝑔(𝑙)) due to exponential offsets. Therefore total no of skip connections is
∑𝑁𝑙=1(𝑙𝑜𝑔𝑐𝑙)=𝑂(𝑁𝑙𝑜𝑔𝑁) 
N is the number of basic blocks (depth) of the network.
The number of parameters are  𝑂(𝑁𝑙𝑜𝑔𝑁)  and  𝑂(𝑁) , respectively, for aggregation by concatenation and aggregation by summation
SparseNets have such skip connections only at depths of  2𝑁 . This allows model to be less memory intensive due to less parameters while still performing equivalent to densnet or better
![alt text](https://lh3.googleusercontent.com/ar5begWFXAGXPVDeIORZB_iD4OrsAe6dR-yyfEjCNhR8fnt-LnnFcRDUrecj7era4845nS8iyolaWmN0GaTCo114I9WmTSTo0cTIGBQnVwzvJ9yrVa0Fm0TYUnxphcHbQC5pAoWe=w2400)
** Densnet/Resnet**
![alt text](https://lh3.googleusercontent.com/pJosUXvPpuMJu87oi0gb351VelsWpLkbcX6TXx5i1qh_QOaMEPgeJS-Ikg3Dilfue6qDNnfOblaOpc8BUJOzgY4yPE23QxOBttS268ojfYJajR7uBGg__cNisOUUIp0f-vNfx7zi=w2400)
![alt text](https://lh3.googleusercontent.com/EnnfenqM7PICFgtcfxgVO0PWJOCbpFFCCq0DDSRhBoZU63ZgZUzqAsGWx0tSZCbULSNwqfBDEr41Q0enZUJXAUON3j2s30aqosQZrrsgBHWHjWJpB4Xo5bBlm-NvmBkkXJNOTRMp=w2400)
** Sparsenet**
