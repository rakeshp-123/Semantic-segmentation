# Semantic Segmentation
### Overview
The goal of this project is to label the road pixels using Fully Connected Neural Network for Semanti segmentation.

### Description
The project code downloads pre-trained VGG16  model and and extracts the input, keep_prob, layer3, layer 4 and layer 7. These layers are used to create the rest of FCN.

#### Architecture
- Convolution layer created using 1x1 kernel and layer 7 extracted from VGG16. (line 61)
- Deconvolution layer created for 2x upsampling using 4x4 kernel and stride 2 from previous convolution layer created(line 66)
- Convolution layer created using 1x1 kernel and layer 4 extracted from VGG16. (line 75)
- skip layer created using the above 2 layers(line 80)
- Deconvolution layer created for 2x upsampling using 4x4 kernel and stride 2 from previous skip layer created(line 82)
- Convolution layer created using 1x1 kernel and layer 3 extracted from VGG16. (line 91)
- skip layer created using the above 2 layers(line 96)
- Deconvolution layer created for 8x upsampling using 16x16 kernel and stride 8 from the last skip layer created(line 98)

All the convolution and deconvolution layer use random kernel initializer with standard deviation 0.01 and L2 regularization  with value 1e-3.

The optimizer used is AdamOptimizer for cross entropy loss and is defined in optimize function (line 128)
The neural network is trained using train_nn function.

The code is trained using 15, 20, 46,48 epochs and i felt 46 epochs were good enough.
The batch size tried were 5,6,10 and I settled with 6.
The loss values are printed while training network and seems to be decresing in value gradually.
The sample images are uploaded in image folder.
