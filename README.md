# GAN-AI-Assignment
> Convert any photos into an Aesthetic Arts

<div>
  <img src='DATA/clear.jpg' height="346px">
  <img src='DATA/style_adopt.jpg' height="346px">
  <img src='DATA/style.jpg' height="346px">
</div>

Stylize Any photo  in the style of famous paintings using Neural Style Transfer.
* This is hundreds of times faster than the optimization-based method presented by [Gatys et al](https://arxiv.org/abs/1508.06576) so-called fast style transfer.
*  We train a feedforward network that applies artistic styles to images using the loss function defined in [Gatys et al](https://arxiv.org/abs/1508.06576) paper.
* Feed forward network is a residual autoencoder network that inputs content image and spits out the stylized image.
* Model also uses instance normalization instead of batch normalization based on the paper [Instance Normalization: The Missing Ingredient for Fast Stylization](https://arxiv.org/abs/1607.08022)
* Training uses perceptual loss defined in the paper [Perceptual Losses for Real-Time Style Transfer and Super-Resolution](https://arxiv.org/abs/1603.08155).
* Vgg19 is used to calculate perceptual loss more closely described on paper.
* find [here](https://drive.google.com/drive/folders/1zHpVh5Sxhb0Z2xwctesmzLydMYTO9C2m?usp=sharing) dataset used in this code.

# Loss Model Setup for Perceptual Loss Calculation
In this implementation, we employ a trained VGG19 model to compute perceptual loss, inspired by the principles outlined in a relevant [paper](https://arxiv.org/abs/1603.08155).

The approach parallels Gatys style transfer, wherein the calculation of style and content loss is pivotal. To derive the total loss, we utilize a pretrained VGG network, passing both style and content images through it. Specific layers of the network are employed to extract features, with higher layers capturing complex features (e.g., representing the face of a dog), preserving essential content. In contrast, lower layers capture smaller features (e.g., eyes, nose, ears), making them suitable for content loss.

For style loss, lower layers of the network are chosen, as they encapsulate learned details like edges and contours, mimicking brush strokes from a painting. Multiple layers are used for style loss to introduce variations in strokes, ensuring a realistic representation.


# Fast Style Transfer Model
Our Fast Style Transfer model employs an encoder-decoder architecture enriched with residual layers. The process involves passing input images through the encoder, which subsequently feeds into the decoder. The decoder generates an image of the same size as the input, serving as the predicted output.

During the training phase, this generated image is forwarded through our loss model, leveraging the capabilities of VGG19. The loss model extracts features from various layers, encompassing both content and style layers. These features play a crucial role in calculating style loss and content loss.

To elaborate, style loss is determined by examining the features from lower layers, capturing fine details such as edges and contours that emulate distinct brush strokes found in paintings. On the other hand, content loss relies on features from higher layers, preserving complex elements and ensuring the fidelity of the generated content.

The final training objective is achieved by computing the weighted sum of style loss and content loss, resulting in the perceptual loss. This perceptual loss guides the training of our network, enhancing its ability to generate visually appealing and stylistically accurate images.

Refer to the illustrative image below for a visual representation of the process:
<div>
  <img src="">
</div>
