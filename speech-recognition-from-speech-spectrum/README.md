# Speech Recognition from Speech Spectrum

## Overview

This project implements an audio digit classification pipeline using the [Free Spoken Digit Dataset (FSDD)](https://www.kaggle.com/datasets/joserzapata/free-spoken-digit-dataset-fsdd). The workflow converts raw audio into Mel-spectrograms, extracts features with a CNN, and evaluates classification performance under different augmentation strategies.

## Notebook

Open the main Jupyter notebook to explore the complete workflow:

```bash
jupyter notebook notebooks/audio_classification.ipynb
```

## Workflow Steps

1. **Data Loading:** Load raw WAV files from FSDD.
2. **Spectrogram Generation:** Convert waveforms to Mel-spectrograms.
3. **Feature Extraction & Classification:** Train a CNN on spectrogram images.
4. **Augmentation Experiments:** Compare:
   - **(a)** Baseline (no augmentation)
   - **(b)** Speech augmentation (noisy/speed-varied audio before spectrogram)
   - **(c)** Spectrum augmentation (time/frequency masks on spectrograms)
   - **(d)** Combined speech + spectrum augmentation

## Usage

1. Clone the repository:

```bash
git clone [https://github.com/Omarkhaled711/deep-learning-projects.git](https://github.com/Omarkhaled711/deep-learning-projects.git); cd deep-learning-projects; cd speech-recognition-from-speech-spectrum;

```

1. Install dependencies:

```bash
pip install -r requirements.txt
```

1. Run the notebook:

```bash

jupyter notebook notebooks/audio\_classification\_workflow\.ipynb

```

## Results Summary

| Experiment | Train Acc | Test Acc | Notes |
|------------|-----------|----------|-------|
| Baseline   | 97.96%    | 96.67%   | Converges slower |
| Speech Aug | 99.54%    | 97.45%   | Faster learning  |
| Spec Aug   | 99.99%    | 97.13%   | Similar speed    |
| Combined   | 99.99%    | 97.XX%   | Fastest learning |
