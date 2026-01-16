[GO TO KAGGLE NOTEBOOK](https://www.kaggle.com/code/abdullahalmamunzihan/simplegan)


# Simple GAN for Speech Enhancement

This repository contains a simple Generative Adversarial Network (GAN) implementation for speech enhancement.  
The purpose of this project is to understand the basic working principles of GANs in the context of audio and speech processing.

Model accuracy or state of the art performance is not the primary target of this implementation.



## Project Objective

The main objectives of this project are:

- To understand how GANs work in a supervised speech enhancement task
- To learn the interaction between Generator and Discriminator networks
- To explore adversarial training using noisy and clean speech pairs
- To visualize and listen to enhanced speech outputs

This project is intended for educational and learning purposes.



## Dataset Assumptions

- Audio files are in WAV format
- Each WAV file contains two channels:
  - Channel 0 represents noisy speech
  - Channel 1 represents clean speech
- Sampling rate must be 16 kHz
- Audio signals are normalized to the range [-1, 1]
- Fixed length segments of 16384 samples are used during training



## Model Architecture

### Generator

- 1D convolutional encoder decoder network
- U-Net style architecture with skip connections
- Takes noisy speech as input
- Outputs enhanced speech waveform
- Uses tanh activation at the output layer

### Discriminator

- Conditional discriminator
- Takes noisy speech and clean or generated speech as input
- Uses 1D convolution layers
- Outputs a probability score indicating real or fake speech



## Training Strategy

- Conditional GAN training
- Discriminator is trained to distinguish real clean speech from generated speech
- Generator is trained to:
  - Fool the discriminator using adversarial loss
  - Minimize L1 loss between generated and clean speech

Total generator loss is the sum of adversarial loss and L1 reconstruction loss.



## Evaluation Metrics

The following metrics are used during testing if reference clean speech is available:

- PESQ for perceptual speech quality
- STOI for speech intelligibility
- SI-SDR for signal distortion measurement

Metrics are optional and training does not depend on them.



## How to USE

1. Noisy and clean audio files are provided in the *training_samples* folder. Each WAV file contains dual channel audio, where one channel represents noisy speech and the other represents clean speech.

2. Update the training directory path according to your local file structure.

3. Change the training parameters in the first cell as needed, then run the notebook and start training.

Now enjoy.

## Limitations

- This is a time domain waveform based GAN
- No STFT or frequency domain processing is used
- Not optimized for real world deployment
- Not intended for high quality speech enhancement benchmarks


## Intended Use

This project is intended for:
- Learning GAN fundamentals
- Academic demonstrations
- Beginner level research exploration
- Understanding adversarial training in audio tasks


## Requirements

- Python 3.8 or higher
- PyTorch
- NumPy
- SciPy
- Matplotlib
- pesq and pystoi (optional for evaluation)


## License

This project is provided for educational purposes.  
Feel free to modify and extend it for learning and research.
