## **Gen Ai for antenna design by Lung-fai Tuen**
I am a graduate Ph.D. student in the ECE Dept. at TKU.
Using seven single-frequency antennas (4 at 2.45 GHz and 3 at 5.2 GHz) as the data source, this data serves as the foundational learning dataset for naturally generated dual-frequency antennas. Utilizing a PGGAN architecture with dimensions ranging from low to high (512x512), the trained neural network model is then used to generate unique dual-frequency antennas.

## The purpose of the paper
The paper on antenna natural generation discusses the evolution of Generative Adversarial Networks (GAN) technology, initially proposed by Ian Goodfellow and colleagues in 2014 as an unsupervised learning model. The basic principle of GAN involves training through two neural networks—the Generator and the Discriminator—engaged in adversarial learning. The Generator attempts to produce fake data resembling real data, while the Discriminator tries to distinguish between the fake data generated by the Generator and the real data. This adversarial process ultimately enables the Generator to produce highly realistic data.

**1. Limitations of Traditional GAN:**
Although the traditional GAN model is conceptually simple, it faces several issues in practical applications, including:
- Mode Collapse: The Generator may focus on generating a small number of high-quality samples, neglecting data diversity.
- Training Instability: Due to imbalances in learning rates between the Generator and the Discriminator, the GAN training process is often unstable, leading to non-convergence or poor results.
- Difficulties in Optimizing the Loss Function: The loss function in traditional GAN, based on the Jensen-Shannon (JS) divergence, can lead to vanishing gradients, particularly in high-dimensional datasets.

**2. WGAN (Wasserstein GAN):**

To address the limitations of traditional GANs, the Wasserstein GAN (WGAN) was introduced. WGAN replaces the JS divergence with the Wasserstein distance (also known as Earth Mover’s Distance), making the training process more stable. Key improvements include:
- A More Stable Loss Function: WGAN calculates the Wasserstein distance between the real and generated data distributions, resulting in smoother gradients and mitigating the vanishing gradient problem.
- Easier-to-Train Model: WGAN uses weight clipping to force both the Generator and Discriminator to remain within reasonable parameter ranges, preventing oscillation and instability during training. To further improve the performance of WGAN, this paper utilizes WGAN-GP (WGAN with Gradient Penalty), where a gradient penalty replaces weight clipping. WGAN-GP introduces a penalty term to enforce the Lipschitz constraint on the Discriminator, maintaining training stability.
Although WGAN provides significant improvements over traditional GAN, it still faces some limitations in practical applications. While WGAN-GP greatly enhances generation quality and training stability, it encounters challenges when generating high-resolution images, especially with complex structures. These challenges include mode collapse, gradient vanishing or explosion, training instability, difficulties in generating fine details, and the computational demands of large datasets. For high resolutions like 512x512, the Generator must learn both macro structures (such as object outlines) and micro details (such as textures and color variations). While WGAN can stably learn lower-dimensional images, such as 4x4, it struggles to generate intricate details at higher resolutions like 512x512, leading to images that appear unnatural or blurry in finer details. These challenges strongly indicate a need for further architectural optimization, loss function improvements, and advanced training methods. To address this, the paper adopts Progressive Growing of GANs (PGGAN), combining WGAN-GP with a strategy of gradually increasing the resolution of both the Generator and Discriminator.

**3. PGGAN (Progressive Growing of GANs):**

To further address the limitations of WGAN, Progressive Growing of GANs (PGGAN) was introduced. PGGAN gradually increases the size of the generating network. The core idea of PGGAN is to start training at a low resolution and progressively increase the resolution of the Generator and Discriminator as training progresses, allowing the GAN to incrementally learn the detailed features of the data. The main advantages of this approach include:
- Higher Image Generation Quality: Gradually increasing the network resolution allows the model to first learn large-scale structures and then progressively refine small-scale details, resulting in clearer and more detailed images.
- More Stable Training Process: The gradual increase in resolution reduces the difficulty of handling high-dimensional data in the early stages, lowering the risk of mode collapse and stabilizing the training process.
- Adaptability to Large Datasets: PGGAN is especially effective for large datasets, as it can learn the diversity of the data step by step through multi-stage training.

**4. The Transition from WGAN to PGGAN:**

In this paper on antenna natural generation, the researchers initially experimented with traditional GAN models but found that the training was unstable and the generated data quality was suboptimal. To overcome these problems, WGAN was introduced, leveraging the stable Wasserstein distance loss function to improve the model's learning capabilities. However, WGAN still encountered bottlenecks when generating high-resolution images on large datasets. Finally, the study adopted PGGAN, which uses the progressive growing technique to enhance the stability and quality of high-dimensional data generation.
The application of PGGAN not only improved the quality of generated data but also significantly reduced training difficulty, allowing the antenna generation model to successfully learn multi-level features and produce more precise antenna structures.

**Conclusion:**

In summary, the technical evolution in this study started with traditional GANs, progressed to WGAN, and ultimately chose PGGAN to address the limitations of traditional GAN and WGAN in generating high-dimensional data. This process demonstrates how iterative technological advancements can resolve common issues in Generative Adversarial Networks, ultimately achieving stable and high-quality antenna natural generation. The paper illustrates how the evolution of GAN technology, from traditional GAN to WGAN, and finally to PGGAN, overcame model shortcomings and achieved stable and high-quality antenna generation. This progression not only solved issues of training instability and insufficient generation quality but also highlighted the importance of technological improvements in enhancing the generation of high-dimensional data.

## UP G/D model h5 format
This dual-band antenna model(ZIP) is free for reader study only.
You can download it for personal use. 
## How to use this model ? 
https://drive.google.com/file/d/14yHSt95wfGdOeqCy5hSNNuSolD0YohSh/view?usp=sharing

After downloading the "antenna.zip" file and generator model(512x512_generator.h5), extract it.
The file is relatively large because I included all the Python-related files that will be imported together.
Please create two directories on the D drive: "antenna_model" and "antenna_samples". The "antenna_model" directory is for storing the model(512x512_generator.h5), and the "antenna_samples" directory is for storing the generated antennas. Finally, Run the execution(antenna.exe). 
The generation of antenna samples is done in multiples of two each times.
## Recently new broadband feature antenna (NEW TRAINING MODEL FOR multi-bb antennas)
three single band antenna(2.45,3.4 and 5.2GHZ) to achieve this whole new bb antenna. One of antenna is included broadband feature.
![image](https://github.com/justintuen/lungfai/blob/main/material/pictures/1.jpg)
![image](https://github.com/justintuen/lungfai/blob/main/material/pictures/2.jpg)
![image](https://github.com/justintuen/lungfai/blob/main/material/pictures/3.jpg)
![image](https://github.com/justintuen/lungfai/blob/main/material/pictures/4.jpg)
![image](https://github.com/justintuen/lungfai/blob/main/material/pictures/5.jpg)
![image](https://github.com/justintuen/lungfai/blob/main/material/pictures/6.jpg)
![image](https://github.com/justintuen/lungfai/blob/main/material/pictures/7.jpg)
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

## ML VS CGAN VS PGGAN
![image](https://github.com/justintuen/lungfai/blob/main/material/pictures/ML_CGAN_PGGAN.png)

PGGAN, Conventional Machine Learning (ML), and CGAN—regarding their performance in antenna design. It evaluates various aspects such as advantages, mathematical basis, efficiency, algorithm, goal, potential, novelty, learning approach, post-learning efficiency, and post-learning novelty.
•	PGGAN is characterized by stable and high-quality generation, though it is time-consuming with lower efficiency. It gradually improves design quality by progressively increasing resolution, making it ideal for high-resolution, complex, and innovative designs.
•	Conventional Machine Learning (ML) focuses on fast optimization and accurate predictions. It is highly efficient and suitable for rapid iterations but may have limited innovation, relying heavily on data and model-driven designs.
•	CGAN is highly flexible, generating diverse designs adaptable to specific conditions. It excels in producing novel and innovative designs, especially under unclear conditions, but stability might decrease in certain scenarios.
The conclusion highlights that PGGAN is best suited for detailed multi-frequency antenna design due to its high-quality output and exploration of novel designs. In contrast, ML is optimal for fast design processes, while CGAN offers flexibility and creativity, generating diverse and innovative designs based on given conditions.

