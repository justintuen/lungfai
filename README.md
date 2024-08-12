# **Lung-fai Tuen**
I am a graduate student in the ECE Dept. at TKU.
Using seven single-frequency antennas (4 at 2.45 GHz and 3 at 5.2 GHz) as the data source, this data serves as the foundational learning dataset for naturally generated dual-frequency antennas. Utilizing a PGGAN architecture with dimensions ranging from low to high (512x512), the trained neural network model is then used to generate unique dual-frequency antennas.
## UP G/D model h5 format
This dual-band antenna model(ZIP) is free for reader study only.
You can download it for personal use.
## Recently new broadband feature antenna
three single band antenna(2.45,3.4 and 5.2GHZ) to achieve this whole new bb antenna. One of antenna is included broadband feature.
![image](https://github.com/justintuen/lungfai/blob/main/material/pictures/bb.jpg)
This broadband antenna is using other bb model.
## Pervious Ai antenna sample
![image](https://github.com/justintuen/lungfai/blob/main/material/pictures/github.jpg)
## Generating speed
![image](https://github.com/justintuen/lungfai/blob/main/material/pictures/bb_g.jpg)
An antenna can be generated every three seconds for experiments.
## Training again
This G/D(512x512) model can be used to training again for new antenna structure updated. 
## G/D layers_block

![image](https://github.com/justintuen/lungfai/blob/main/material/pictures/dis_block.png)

This image shows the architectural details of a discriminator model named "model_1," commonly used in Generative Adversarial Networks (GANs). The content includes the name of each layer, the output shape, the number of parameters, and the connections between layers. Here's a breakdown of the main points:

1. **Model Layer Structure**: The image displays each layer in the model, starting from the input layer (`input_2`) to the output layer (`output_dense`). The layers include convolutional layers (`conv2d`), activation layers (`Activation`), pooling layers (`AveragePooling2D`), equalized learning rate layers (`EqualizeLearningRate`), subtraction layers (`TFOpLambda`), and minibatch standard deviation layers (`MinibatchStdev`), among others.

2. **Output Shape**: The output shape of each layer represents the shape of the tensor output by that layer. For example, the input layer has an output shape of `(None, 512, 512, 3)`, meaning the batch size is undefined (`None`), the spatial dimensions are 512x512, and there are 3 channels (likely RGB images).

3. **Number of Parameters (Param #)**: This indicates the number of parameters that need to be trained in each layer. These parameters determine the complexity of the model. For example, the `Down_512x512_conv2d_2` layer has 18,497 parameters.

4. **Connections Between Layers**: The `Connected to` column describes where each layer's input comes from, i.e., the preceding layers. For instance, the `activation_14` layer's input comes from the `Down_512x512_conv1d_1` layer.

5. **Model Parameter Summary**:
   - Total parameters (`Total params`): 23,070,516
   - Trainable parameters (`Trainable params`): 23,070,497
   - Non-trainable parameters (`Non-trainable params`): 19

![image](https://github.com/justintuen/lungfai/blob/main/material/pictures/gen_block.png)

This image presents the architectural details of a generator model named "model_1," typically used in Generative Adversarial Networks (GANs). It includes information on each layer's name, output shape, the number of parameters, and the connections between the layers. Here's a detailed explanation:

1. **Model Layer Structure**: The image outlines the layers of the model, starting from the input layer (`input_1`) to the final output layers (`to_rgb_512x512` and `add`). The layers in this model include dense layers (`g_input_dense`), reshaping layers (`Reshape`), convolutional layers (`EqualizeLearningRate`), pixel normalization layers (`PixelNormalization`), activation layers (`LeakyReLU`, `Activation`), upsampling layers (`Upsampling2D`), and addition/multiplication layers (`Add`, `Multiply`), among others.

2. **Output Shape**: The output shape of each layer specifies the shape of the tensor produced by that layer. For example, the input layer has an output shape of `(None, 512)`, meaning the batch size is undefined (`None`), and the tensor has 512 elements.

3. **Number of Parameters (Param #)**: This shows the number of parameters to be trained for each layer. For instance, the `g_input_dense` layer has 4,204,297 parameters, indicating its significant role in the model's complexity.

4. **Connections Between Layers**: The `Connected to` column indicates how each layer is connected to previous layers. For example, the `leaky_re_lu_1` layer takes its input from the `g_input_dense` layer.

5. **Model Parameter Summary**:
   - Total parameters (`Total params`): 25,423,046
   - Trainable parameters (`Trainable params`): 25,423,046
   - Non-trainable parameters (`Non-trainable params`): 0

## G/D loss value
![image](https://github.com/justintuen/lungfai/blob/main/material/pictures/loss_plot.png)
Based on the generated learning curves of the Generator and Discriminator Loss values for PGGAN (Progressive Growing of GANs), the following characteristics can be observed:
Learning Characteristics Analysis
Volatility of G_Loss and D_Loss
-	The plot shows that both G_Loss (red solid line) and D_Loss (green dashed line) exhibit significant fluctuations throughout the training process.
-	G_Loss shows more pronounced fluctuations compared to D_Loss, indicating more dramatic changes.
  Initial Phase (0 - 1000 steps)
-	During the initial phase of training (approximately 0 to 1000 steps), both Loss values display considerable fluctuations as the model's parameters undergo significant updates.
-	Both the Generator and Discriminator are striving to find suitable parameter ranges to generate and recognize images.
  Mid Phase (1000 - 3000 steps)
-	During this period, G_Loss continues to fluctuate significantly, while D_Loss remains relatively stable, suggesting that the Discriminator is consistently able to evaluate the realism of generated images.
-	The high volatility of the Generator indicates that it is continually adjusting to produce more realistic images in an attempt to fool the Discriminator.
  Later Phase (after 3000 steps)
-	In the later stages of training, the fluctuations in Loss values gradually decrease but still show some variations.
-	This indicates that the model is stabilizing but continues to make fine-tuned adjustments.
Significance of Each Phase
- Initial Phase: The model's parameters are adjusting from random values to meaningful ones, attempting to initially learn the basic features of image generation and recognition.
- Mid Phase: The generative and recognition capabilities of the model gradually improve, with the Generator striving to create more realistic images to outsmart the Discriminator.
- Later Phase: The model undergoes further fine-tuning, with reduced Loss value variations, approaching a state of convergence where the quality and realism of generated images reach a higher level.
## Conclusion
From the plot, it is evident that during the training of PGGAN, the Generator's Loss value exhibits significant volatility, reflecting its continuous exploration and adjustment to generate high-quality images. In contrast, the Discriminator's Loss value shows smaller fluctuations, indicating more stable image recognition. Overall, the model gradually converges during training, demonstrating PGGAN's capability to effectively learn and progressively improve the quality of generated images.

## Ai GAN vs Tradiational EM Wave
![image](https://github.com/justintuen/lungfai/blob/main/material/pictures/numerical_comparison.png)

Summary of Benefits Using AI GAN for Dual-Band Antenna Design
1.	Time Efficiency:
Initial Training: Although the initial training takes 384 hours, the GAN model can generate designs extremely quickly once trained.
Rapid Design Generation: The model can produce a single design in 3 seconds, making it possible to generate 10,000 designs in just 8.33 hours. Traditional methods cannot match this speed, as generating 10,000 designs would take an impractical amount of time (approximately 10,000 hours assuming 1 hour per simulation).
2.	Computational Cost:
Initial Training Cost: High due to the need for a powerful GPU and CPU setup.
Low Generation Cost: After training, the resource cost for generating each design is very low, making it highly efficient for large-scale design explorations.
3.	Iteration Speed:
Fast Iterations: Each iteration takes only 3 seconds with the AI GAN model, allowing for quick optimization cycles.
Traditional Methods: Each iteration with traditional methods takes significantly longer (30 minutes to 2 hours), making the optimization process much slower.

## Conclusion
1. Efficiency Advantage: The AI GAN model significantly outperforms traditional EM wave simulation in terms of speed and efficiency, allowing for rapid generation and evaluation of a large number of designs.
2. Cost Advantage: Despite the high initial training cost, the ongoing cost of generating new designs is extremely low, making it very cost-effective for extensive design exploration.
3. Iteration Advantage: The AI GAN method enables rapid iterations, facilitating quick optimizations and adjustments, which is critical for innovative and high-performance antenna designs.
In this paper, we are using the AI GAN antenna design method provides designers with substantial benefits in terms of efficiency, cost, and iteration speed, compared to traditional EM wave simulation methods. This approach significantly enhances the overall effectiveness and innovation capability of the antenna design process.

