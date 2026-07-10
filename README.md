# Image Forgery Detection using Wasserstein Generative Adversarial Network (WGAN)

## Overview

This project implements a **Wasserstein Generative Adversarial Network (WGAN)** using **PyTorch** for image forgery analysis and synthetic image generation. The model learns the distribution of real images and generates realistic forged-like images while improving the discriminator's ability to distinguish between real and generated samples.

The project can be used for:

* Image Forgery Detection Research
* Synthetic Image Generation
* Deep Learning Experiments using GANs
* Data Augmentation for Image Classification Tasks
* Understanding WGAN Architecture and Training

---

## Features

* Wasserstein GAN (WGAN) implementation
* PyTorch-based architecture
* Custom Generator and Discriminator networks
* Automatic image generation during training
* Model checkpoint saving
* GPU acceleration support (CUDA)
* Dataset loading using ImageFolder
* Training loss monitoring
* Sample image visualization

---

## Project Structure

```text
├── WGAN_new.ipynb               # Training Notebook
├── test_wgan.ipynb              # Testing Notebook
├── generated_images/            # Generated Images
├── discriminator_models/        # Saved Discriminator Models
├── samples/                     # Training Samples
├── models/                      # Saved Model Checkpoints
├── G.ckpt                       # Generator Model
├── D.ckpt                       # Discriminator Model
└── README.md
```

---

## Technologies Used

* Python 3.x
* PyTorch
* TorchVision
* NumPy
* Matplotlib
* PIL (Python Imaging Library)
* Google Colab

---

## Model Architecture

### Generator

The Generator receives a random noise vector and produces a synthetic image.

Architecture:

```text
Input Noise (100)

↓ ConvTranspose2D
↓ BatchNorm
↓ ReLU

↓ ConvTranspose2D
↓ BatchNorm
↓ ReLU

↓ ConvTranspose2D
↓ BatchNorm
↓ ReLU

↓ ConvTranspose2D
↓ BatchNorm
↓ ReLU

↓ ConvTranspose2D
↓ Tanh

Output Image (64×64×3)
```

---

### Discriminator (Critic)

The Critic evaluates whether an image is real or generated.

Architecture:

```text
Input Image (64×64×3)

↓ Conv2D
↓ LeakyReLU

↓ Conv2D
↓ BatchNorm
↓ LeakyReLU

↓ Conv2D
↓ BatchNorm
↓ LeakyReLU

↓ Conv2D
↓ BatchNorm
↓ LeakyReLU

↓ Conv2D

Output Score
```

---

## Hyperparameters

```python
LEARNING_RATE = 5e-5
BATCH_SIZE = 64
IMAGE_SIZE = 64
CHANNELS_IMG = 3
NOISE_DIM = 100
NUM_EPOCHS = 1000
FEATURES_DISC = 64
FEATURES_GEN = 64
```

---

## Dataset

The dataset is organized using the PyTorch ImageFolder format:

```text
Dataset/
│
├── Class_1/
│   ├── image1.jpg
│   ├── image2.jpg
│   └── ...
│
├── Class_2/
│   ├── image1.jpg
│   ├── image2.jpg
│   └── ...
```

Images are resized to:

```text
64 × 64 pixels
```

and normalized to:

```text
[-1, 1]
```

---

## Installation

Clone the repository:

```bash
git clone https://github.com/your-username/wgan-image-forgery-detection.git
cd wgan-image-forgery-detection
```

Install dependencies:

```bash
pip install torch torchvision numpy matplotlib pillow
```

---

## Training

Open the notebook:

```bash
jupyter notebook WGAN_new.ipynb
```

or run in Google Colab.

Training process:

1. Load dataset
2. Initialize Generator and Discriminator
3. Train Critic
4. Train Generator
5. Save generated images
6. Save model checkpoints

---

## Testing

Load the trained model:

```python
generator.load_state_dict(torch.load("G.ckpt"))
generator.eval()
```

Generate new images:

```python
noise = torch.randn(1,100,1,1)
generated_image = generator(noise)
```

---

## Results

During training:

* Fake images are generated after every epoch.
* Generator learns realistic image patterns.
* Discriminator improves its ability to identify real and fake images.
* Model checkpoints are saved periodically.

Generated samples are stored in:

```text
generated_images/
```

Saved models are stored in:

```text
models/
```

---

## Applications

* Deepfake Analysis
* Image Forgery Detection
* Synthetic Dataset Generation
* Medical Image Augmentation
* Cyber Security Research
* Digital Forensics

---

## Future Enhancements

* WGAN-GP Implementation
* Conditional GAN Support
* Higher Resolution Images
* Improved Evaluation Metrics
* Web-based Deployment
* Real-time Forgery Detection

---

## Author

**Tejashree Kumar**

AI/ML Engineer | SME | Assistant Professor

Research Interests:

* Deep Learning
* Computer Vision
* Generative AI
* Image Forensics
* Medical Image Analysis

---

## License

This project is intended for educational and research purposes.
Feel free to modify and extend the implementation for academic research and experimentation.
