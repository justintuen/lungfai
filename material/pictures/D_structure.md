Here is a detailed table summarizing all the layers of the discriminator model along with their descriptions:

| Layer Name                   | Layer Type            | Output Shape         | Parameters  | Connected To                    | Description                              |
|------------------------------|-----------------------|----------------------|-------------|---------------------------------|------------------------------------------|
| input_2                      | InputLayer            | (None, 512, 512, 3)  | 0           |                                 | Input layer for images of size 512x512x3 |
| from_rgb_512x512             | EqualizeLearningRate  | (None, 512, 512, 32) | 129         | input_2                         | Converts RGB input to feature maps       |
| Down_512x512_conv2d_1        | EqualizeLearningRate  | (None, 512, 512, 32) | 9249        | from_rgb_512x512                | Convolution layer with equalized learning rate to extract features |
| activation_14                | Activation            | (None, 512, 512, 32) | 0           | Down_512x512_conv2d_1           | Applies activation function to introduce non-linearity |
| Down_512x512_conv2d_2        | EqualizeLearningRate  | (None, 512, 512, 64) | 18497       | activation_14                   | Another convolution layer to extract deeper features |
| input_alpha                  | InputLayer            | (None, 1)            | 0           |                                 | Input layer for blending parameter     |
| average_pooling2d            | AveragePooling2D      | (None, 256, 256, 3)  | 0           | input_2                         | Downsamples input to reduce spatial resolution |
| activation_15                | Activation            | (None, 512, 512, 64) | 0           | Down_512x512_conv2d_2           | Applies activation function            |
| tf.math.subtract_1           | TFOpLambda            | (None, 1)            | 0           | input_alpha                     | Performs subtraction operation, used for blending |
| from_rgb_256x256             | EqualizeLearningRate  | (None, 256, 256, 64) | 257         | average_pooling2d               | Converts downsampled RGB input to feature maps |
| average_pooling2d_1          | AveragePooling2D      | (None, 256, 256, 64) | 0           | activation_15                   | Further downsamples the feature maps    |
| multiply_2                   | Multiply              | (None, 256, 256, 64) | 0           | tf.math.subtract_1, from_rgb_256x256 | Multiplies input values for blending purposes |
| multiply_3                   | Multiply              | (None, 256, 256, 64) | 0           | input_alpha, average_pooling2d_1| Multiplies input values for blending purposes |
| add_1                        | Add                   | (None, 256, 256, 64) | 0           | multiply_2, multiply_3          | Adds two inputs for blended feature maps |
| Down_256x256_conv2d_1        | EqualizeLearningRate  | (None, 256, 256, 64) | 36929       | add_1                           | Convolution layer after blending       |
| activation_16                | Activation            | (None, 256, 256, 64) | 0           | Down_256x256_conv2d_1           | Applies activation function            |
| Down_256x256_conv2d_2        | EqualizeLearningRate  | (None, 256, 256, 128)| 73857       | activation_16                   | Convolution layer for further feature extraction |
| activation_17                | Activation            | (None, 256, 256, 128)| 0           | Down_256x256_conv2d_2           | Applies activation function            |
| average_pooling2d_2          | AveragePooling2D      | (None, 128, 128, 128)| 0           | activation_17                   | Downsamples feature maps               |
| Down_128x128_conv2d_1        | EqualizeLearningRate  | (None, 128, 128, 128)| 147585      | average_pooling2d_2             | Convolution layer for feature extraction at lower resolution |
| activation_18                | Activation            | (None, 128, 128, 128)| 0           | Down_128x128_conv2d_1           | Applies activation function            |
| Down_128x128_conv2d_2        | EqualizeLearningRate  | (None, 128, 128, 256)| 295169      | activation_18                   | Further convolution layer for feature extraction |
| activation_19                | Activation            | (None, 128, 128, 256)| 0           | Down_128x128_conv2d_2           | Applies activation function            |
| average_pooling2d_3          | AveragePooling2D      | (None, 64, 64, 256)  | 0           | activation_19                   | Downsamples feature maps               |
| Down_64x64_conv2d_1          | EqualizeLearningRate  | (None, 64, 64, 256)  | 590081      | average_pooling2d_3             | Convolution layer for feature extraction at 64x64 resolution |
| activation_20                | Activation            | (None, 64, 64, 256)  | 0           | Down_64x64_conv2d_1             | Applies activation function            |
| Down_64x64_conv2d_2          | EqualizeLearningRate  | (None, 64, 64, 512)  | 1180161     | activation_20                   | Convolution layer for deeper feature extraction |
| activation_21                | Activation            | (None, 64, 64, 512)  | 0           | Down_64x64_conv2d_2             | Applies activation function            |
| average_pooling2d_4          | AveragePooling2D      | (None, 32, 32, 512)  | 0           | activation_21                   | Downsamples feature maps               |
| Down_32x32_conv2d_1          | EqualizeLearningRate  | (None, 32, 32, 512)  | 2359809     | average_pooling2d_4             | Convolution layer for feature extraction at 32x32 resolution |
| activation_22                | Activation            | (None, 32, 32, 512)  | 0           | Down_32x32_conv2d_1             | Applies activation function            |
| Down_32x32_conv2d_2          | EqualizeLearningRate  | (None, 32, 32, 512)  | 2359809     | activation_22                   | Further convolution layer for feature extraction |
| activation_23                | Activation            | (None, 32, 32, 512)  | 0           | Down_32x32_conv2d_2             | Applies activation function            |
| average_pooling2d_5          | AveragePooling2D      | (None, 16, 16, 512)  | 0           | activation_23                   | Downsamples feature maps               |
| Down_16x16_conv2d_1          | EqualizeLearningRate  | (None, 16, 16, 512)  | 2359809     | average_pooling2d_5             | Convolution layer for feature extraction at 16x16 resolution |
| activation_24                | Activation            | (None, 16, 16, 512)  | 0           | Down_16x16_conv2d_1             | Applies activation function            |
| Down_16x16_conv2d_2          | EqualizeLearningRate  | (None, 16, 16, 512)  | 2359809     | activation_24                   | Further convolution layer for feature extraction |
| activation_25                | Activation            | (None, 16, 16, 512)  | 0           | Down_16x16_conv2d_2             | Applies activation function            |
| average_pooling2d_6          | AveragePooling2D      | (None, 8, 8, 512)    | 0           | activation_25                   | Downsamples feature maps               |
| Down_8x8_conv2d_1            | EqualizeLearningRate  | (None, 8, 8, 512)    | 2359809     | average_pooling2d_6             | Convolution layer for feature extraction at 8x8 resolution |
| activation_26                | Activation            | (None, 8, 8, 512)    | 0           | Down_8x8_conv2d_1               | Applies activation function            |
| Down_8x8_conv2d_2            | EqualizeLearningRate  | (None, 8, 8, 512)    | 2359809     | activation_26                   | Further convolution layer for feature extraction |
| activation_27                | Activation            | (None, 8, 8, 512)    | 0           | Down_8x8_conv2d_2               | Applies activation function            |
| average_pooling2d_7          | AveragePooling2D      | (None, 4, 4, 512)    | 0           | activation_27                   | Downsamples feature maps               |
| minibatch_stddev            | MinibatchSTDDEV      | (None, 4, 4, 513)   | 0           | average_pooling2d_7            | Calculates minibatch standard deviation for regularization |
| d_output_conv2d_1           | EqualizeLearningRate | (None, 4, 4, 512)   | 2364417    | minibatch_stddev               | Convolution layer for final feature extraction |
| leaky_re_lu_2               | LeakyReLU            | (None, 4, 4, 512)   | 0          | d_output_conv2d_1              | Applies leaky ReLU activation function |
| d_output_conv2d_2           | EqualizeLearningRate | (None, 1, 1, 512)   | 4194817    | leaky_re_lu_2                  | Final convolution layer before output |
| leaky_re_lu_3               | LeakyReLU            | (None, 1, 1, 512)   | 0          | d_output_conv2d_2              | Applies leaky ReLU activation function |
| flatten                    | Flatten              | (None, 512)         | 0          | leaky_re_lu_3                  | Flattens the output for dense layer   |
| d_output_dense             | EqualizeLearningRate | (None, 1)           | 514        | flatten                        | Fully connected layer for final output prediction |

