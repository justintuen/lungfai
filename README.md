# Lungfai Tuen
I am a graduate student in the ECE Dept. at TKU.
Using seven single-frequency antennas (4 at 2.45 GHz and 3 at 5.2 GHz) as the data source, this data serves as the foundational learning dataset for naturally generated dual-frequency antennas. Utilizing a PGGAN architecture with dimensions ranging from low to high (512x512), the trained neural network model is then used to generate unique dual-frequency antennas.
# UP G/D model h5 format
This dual-band antenna model(ZIP) is free for reader study only.
You can download it for personal use.
# Recently new broadband feature antenna
three single band antenna(2.45,3.4 and 5.2GHZ) to achieve this whole new bb antenna. One of antenna is included broadband feature.
![image](https://github.com/justintuen/lungfai/blob/main/bb.jpg)
This broadband antenna is using other bb model.
# Generating speed
![image](https://github.com/justintuen/lungfai/blob/main/bb_g.jpg)
An antenna can be generated every three seconds for experiments.
# Training again
This G/D(512x512) model can be used to training again for antenna updated.   
# G/D loss value
![image](https://github.com/justintuen/lungfai/blob/main/loss_plot.png)
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
  Initial Phase: The model's parameters are adjusting from random values to meaningful ones, attempting to initially learn the basic features of image generation and recognition.
  Mid Phase: The generative and recognition capabilities of the model gradually improve, with the Generator striving to create more realistic images to outsmart the Discriminator.
  Later Phase: The model undergoes further fine-tuning, with reduced Loss value variations, approaching a state of convergence where the quality and realism of generated images reach a higher level.
Conclusion
From the plot, it is evident that during the training of PGGAN, the Generator's Loss value exhibits significant volatility, reflecting its continuous exploration and adjustment to generate high-quality images. In contrast, the Discriminator's Loss value shows smaller fluctuations, indicating more stable image recognition. Overall, the model gradually converges during training, demonstrating PGGAN's capability to effectively learn and progressively improve the quality of generated images.
