# Residual block in Keras

### NOTICE
* 14 Apr 2016 - `Example.py` is working well.
* 14 Apr 2016 - Updated regarding Keras1.0

### The original articles
 * [Deep Residual Learning for Image Recognition](http://arxiv.org/abs/1512.03385) (the 2015 ImageNet competition winner)
 * [Identity Mappings in Deep Residual Networks](http://arxiv.org/abs/1603.05027) (an update).

### Keras
This implementation is based on [Keras](https://github.com/fchollet/keras).

### MNIST example

`$ python example.py` to run an example code in [`example.py`](https://github.com/keunwoochoi/residual_block_keras/blob/master/example.py). It loads MNIST dataset and
 * add zeropadding `(2,2)` to convert the size `(28,28)` to `(32,32)`
 * add residual blocks
 * add average pooling
 * and add the final output layer.

There are some changes on the block, which you can easily detect. Such as...
 * I put `1x1` convolution, as one of the things tested on the [original article](http://arxiv.org/abs/1512.03385) to extend the `num_feature_map`. There are simpler solution in the paper - which is just pad zeros, and worked well, FYI.
 * The block is updated according to the authors' new paper, [Identity Mappings in Deep Residual Networks](http://arxiv.org/abs/1603.05027).

I had this result:
```
Train on 60000 samples, validate on 10000 samples
Epoch 1/12
60000/60000 [==========] - 1442s - loss: 0.1520 - acc: 0.9525 - val_loss: 0.0826 - val_acc: 0.9728
Epoch 2/20
60000/60000 [==========] - 1350s - loss: 0.0489 - acc: 0.9850 - val_loss: 0.0380 - val_acc: 0.9882
Epoch 3/20
60000/60000 [==========] - 1330s - loss: 0.0377 - acc: 0.9881 - val_loss: 0.1047 - val_acc: 0.9681
Epoch 4/20
60000/60000 [==========] - 1315s - loss: 0.0320 - acc: 0.9897 - val_loss: 0.0483 - val_acc: 0.9839
Epoch 5/20
60000/60000 [==========] - 1352s - loss: 0.0279 - acc: 0.9912 - val_loss: 0.0750 - val_acc: 0.9739
Epoch 6/20
60000/60000 [==========] - 1329s - loss: 0.0263 - acc: 0.9914 - val_loss: 0.0445 - val_acc: 0.9864
Epoch 7/20
60000/60000 [==========] - 1324s - loss: 0.0212 - acc: 0.9934 - val_loss: 0.0316 - val_acc: 0.9899
Epoch 8/20
60000/60000 [==========] - 1360s - loss: 0.0182 - acc: 0.9941 - val_loss: 0.0518 - val_acc: 0.9859
Epoch 9/20
60000/60000 [==========] - 1342s - loss: 0.0188 - acc: 0.9938 - val_loss: 0.0228 - val_acc: 0.9919
Epoch 10/20
60000/60000 [==========] - 1335s - loss: 0.0152 - acc: 0.9949 - val_loss: 0.0289 - val_acc: 0.9916
Epoch 11/20
60000/60000 [==========] - 1330s - loss: 0.0120 - acc: 0.9965 - val_loss: 0.0289 - val_acc: 0.9914
Epoch 12/20
60000/60000 [==========] - 1355s - loss: 0.0132 - acc: 0.9954 - val_loss: 0.0272 - val_acc: 0.9914
Epoch 13/20
60000/60000 [==========] - 1333s - loss: 0.0112 - acc: 0.9965 - val_loss: 0.0238 - val_acc: 0.9923
Epoch 14/20
60000/60000 [==========] - 1336s - loss: 0.0086 - acc: 0.9970 - val_loss: 0.0291 - val_acc: 0.9917
Epoch 15/20
60000/60000 [==========] - 1337s - loss: 0.0108 - acc: 0.9964 - val_loss: 0.0274 - val_acc: 0.9914
Epoch 16/20
60000/60000 [==========] - 1354s - loss: 0.0074 - acc: 0.9977 - val_loss: 0.0246 - val_acc: 0.9928
```
