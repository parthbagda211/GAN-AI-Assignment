# GAN-AI-Assignment
> Convert any photos and videos into an artwork

<div>
  <img src='data/images/style.jpg' height="346px">
  <img src='data/images/content.jpg' height="346px">
  <img src='output/styled.jpg' height="512px">
</div>

Stylize any photo or video in style of famous paintings using Neural Style Transfer.
* This is hundreds of times faster than the optimization-based method presented by [Gatys et al](https://arxiv.org/abs/1508.06576) so called fast style transfer.
*  We train a feedforward network that apply artistic styles to images using loss function defined in [Gatys et al](https://arxiv.org/abs/1508.06576) paper.
* Feed forward network is a residual autoencoder network that takes content image as input and spits out stylized image.
* Model also uses instance normalization instead of batch normalization based on the paper [Instance Normalization: The Missing Ingredient for Fast Stylization](https://arxiv.org/abs/1607.08022)
* Training is done by using perceptual loss defined in paper [Perceptual Losses for Real-Time Style Transfer and Super-Resolution](https://arxiv.org/abs/1603.08155).
* Vgg19 is used to calculate perceptual loss more working described on paper.
