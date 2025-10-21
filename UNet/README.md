# <u> U- Net Architecture
This repo contains:
1. UNet report - model architecture description, inference of implementation
2. U- Net code (available as jupyter notebook and pdf)
3. Results 
4. The dataset used - CARVANA DATASET (from kaggle) - https://github.com/shimchu/carvana-dataset



To run inference: 
# **U \- Net:**                 

The name U \- Net comes from its encoding- decoding architecture that looks like a U.   
**Intuition:**   
The above image shows U-Net turning a 572×572 image into a smaller 388×388 segmented map. It shrinks the image to capture features then upsamples to restore size using skip connections to keep details. The output labels each pixel as object or background.

**Architecture:**  
**1\. Contracting Path (Encoder):**  
Uses small filters (3×3 pixels) to scan the image and find features.  
Apply an activation function called ReLU to add non-linearity help the model to learn better.  
Uses max pooling (2×2 filters) to shrink the image size while keeping important information. This helps the network focus on bigger features.

**2\. Bottleneck:**  
The middle of the “U” where the most compressed and abstract information is stored. It links the encoder and decoder.

**3\. Expansive Path (Decoder):**  
Uses upsampling i.e increasing image size to get back the original image size.  
Combines information from the encoder using “skip connections.” These connections help the decoder get spatial details that might have been lost when shrinking the image  
Uses convolution layers again to clean up and refine the output.

4\. **Skip Connections for Precision**: Skip connections help preserve spatial accuracy by bringing forward detailed features from earlier layers. These are especially useful when the model needs to distinguish boundaries in segmentation tasks.

**Implementation:**  
We implemented the model only using pytorch’s nn.module, creating a class called U\_net and defining the blocks. ![][image1]

We trained it on the carvana dataset (80:20 split for train and test data), for 20 epochs, Adam Optimizer and Binary Cross Entropy as the loss function.

**Finally we achieved an accuracy of : Epoch 20/20, :Test Loss: 0.0238, Test Accuracy: 0.9670**

**Visualizing Random Outputs against ground truth:**

We had good results, further improvements can be made using more skip connections and a deeper network.

Additionally I also proceeded to visualise each and every block in the U Net Architecture:
