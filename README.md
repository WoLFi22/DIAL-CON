# DIAL-CON – _DIAlect Level CONtinuum analyzer_

This repository provides a pipeline for dialect classification using deep learning on raw audio files.  
The pipeline is designed to:

1. Train a model to distinguish between **standard** and **dialectal** speech across multiple speakers.
2. Fine-tune the model on a **specific speaker** to personalize the classification.
3. During inference, evaluate incoming speech segments (e.g., every few seconds or milliseconds) to determine **how dialectal** the speaker is speaking, on a continuous scale relative to their own speech patterns.

The system leverages a pretrained Google model to extract audio embeddings from fixed-length segments, which are then classified using a lightweight Convolutional Neural Network (CNN).

![VertClas](https://github.com/user-attachments/assets/76389431-21e2-4735-a4c3-d2bab87d57bb)

### Key Features
- Easily Adjustable Parameters: The main parameters are easily customizable, allowing for repeated use of the pipeline and facilitating experimentation.
- Results Visualization: Contains a notebook that saves all results as graphics from a test.
- User-Friendly Execution: Everything is set up to run simply by executing the main file with correctly set parameters.
- Optimized for GPU: The pipeline is designed to run on a GPU to accelerate computations.

### Getting Started
- Adjust Parameters: Configure the key parameters in the '_00_Pipeline' file to suit your experiment.
- Run the Pipeline: Execute the '_00_Pipeline' notebook to process the audio data, perform classification, and visualize results.
- Analyze Results: Once the pipeline has finished running, you only need to analyze the results. :wink:

### Contents

- [Requirements](#requirements)
- [Folder structure](#folder-structure)
- [Audio Specifications](#audio-specifications)
- [Usage Instructions](#usage-instructions)


## Requirements

This pipeline has been tested with the following versions:

### Main Dependencies
- ipynb                        0.5.1
- keras                        2.10.0
- librosa                      0.9.2
- matplotlib                   3.5.2
- numpy                        1.22.4
- pandas                       1.4.3
- praat-parselmouth            0.4.3
- pydub                        0.25.1
- python                       3.9.12
- scipy                        1.8.1
- seaborn                      0.11.2
- tensorflow                   2.10.0
- tensorflow-hub               0.13.0

### Additional Dependencies for Preprocessing and Augmentation
- audiomentations              0.30.0
- noisereduce                  3.0.0
- praat (program)              6.2.14
- pyloudnorm                   0.1.1
- soundfile                    0.12.1

### GPU Support
For GPU support, you will need:
- An Nvidia GPU (tested with <em>NVIDIA GeForce RTX 3080 Ti Laptop GPU</em>)
- [CUDA Toolkit](https://developer.nvidia.com/cuda-toolkit) (tested with version 11.2)
- [cuDNN](https://developer.nvidia.com/cudnn) (tested with version 8.9.3)

For compute capability for your Nvidia GPU see [here](https://developer.nvidia.com/cuda-gpus).


### Installation

To install the required packages, you can use the following command:

```bash
pip install -r requirements.txt
```

## Folder structure

<em>Paths are currently only working on Windows-Systems!</em>

This repository follows a specific structure for organizing audio data:
- **Audio Folder**: All audio files should be stored in a designated folder.
- **Subfolders**: Within the audio folder, there should be subfolders named after the dialects of the audio data.
- **Speaker Subfolders**: Inside each class subfolder, create subfolders for the individual speakers from whom the audios are collected.
- **Audios per Speaker**: Each speaker subfolder must contain exactly three audio files, named consistently:
  - the speaker's version of standard (non-dialectal) speech
  - the speaker's version in their native dialect
  - a sample used for testing or evaluation

```
Audio_Folder
│
├── Class_1
│   ├── Speaker_A
│   │   └── audio_1_FreeSpeech.wav
│   │   └── audio_1_Dialect.wav
│   │   └── audio_1_Standard.wav
│   └── Speaker_B
│       └── audio_2_FreeSpeech.wav
│       └── audio_2_Dialect.wav
│       └── audio_2.wav
│
└── Class_2
    ├── Speaker_C
    │   └── audio_3_FreeSpeech.wav
    │   └── audio_3_Dialect.wav
    │   └── audio_3_Standard.wav    
    └── Speaker_D
        └── audio_4_FreeSpeech.wav
        └── audio_4_Dialect.wav
        └── audio_4_Standard.wav

```

## Audio Specifications

To ensure the pipeline operates correctly, the audio files should exhibit the following properties:
- **Mono Format**: Ensure that all audio files are in mono format.
- **Sampling Rate**: Set the sampling rate of the audio files to 16 kHz.
- **Bit Depth**: Verify that the audio files have a bit depth of 16-bit.

For preprocessing the audio data accordingly, refer to the 'Preprocessing' notebook provided in this repository. It contains instructions and code for any necessary preprocessing steps.

## Usage Instructions

All parameters that can be adjusted are listed and described in the `_00_Pipeline.ipynb` file. Once all parameters are correctly filled in, the `_00_Pipeline.ipynb` notebook can be executed.

Additionally, the most important functions in the individual notebooks are described with their parameters in the notebooks itself, even if these do not need to be changed for execution.

<!-- ## Citation / ## Published Papers -->
