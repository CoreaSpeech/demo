# CoreaSpeech: Korean Speech Corpus via JAMO-based Coreset Selection

[![arXiv](https://img.shields.io/badge/arXiv-240X.XXXXX-b31b1b.svg)](https://arxiv.org/abs/240X.XXXXX) <!-- 실제 arXiv ID로 교체해주세요 -->
[![HuggingFace Datasets](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Datasets-blue)](https://huggingface.co/datasets/aanonyyy) <!-- 실제 HuggingFace 링크로 교체해주세요 -->
[![GitHub](https://img.shields.io/github/stars/CoreaSpeech/CoreaSpeech?style=social)](https://github.com/CoreaSpeech/CoreaSpeech) <!-- 실제 GitHub 링크로 교체해주세요 -->

<div align="center">
  <img width="700px" src="./sample/images/Coreaspeech_pipeline.png" /> <!-- 대표 이미지 링크 (현재 파이프라인 이미지로 설정) -->
</div>

## News
- **2025/05/15**: CoreaSpeech dataset, pipeline code, PEFT-TTS model, and Korean Universal Benchmark released!

## Overview
CoreaSpeech is a large-scale Korean speech corpus built via a novel JAMO-based coreset selection pipeline. This project aims to provide an efficient and robust dataset for Korean speech generation and other speech-related tasks. Our pipeline focuses on data refinement, textual normalization, and a unique coreset selection strategy leveraging linguistic and phonological features of Korean.

### Key Features
- **Large-Scale Corpus**: 700 hours of speech data from 21,449 speakers.
- **JAMO-based Coreset Selection**: Efficiently selects a diverse and representative subset of data.
- **Korean-Specific Text Normalization**: Handles numerals, English words, and special characters.
- **Universal Korean TTS Benchmark**: Includes clean, noisy, and numeric test sets.
- **Open Source**: Publicly available dataset, pipeline code, and benchmarks under the CC BY-NC 4.0 license.

### (Optional) Language & Domain Statistics
| Category        | Description                                  | Details                                      |
|-----------------|----------------------------------------------|----------------------------------------------|
| Language        | Korean                                       | Primarily standard Korean accents            |
| Total Hours     | 700 hours                                   | Selected from ~2000+ hours of raw data       |
| Speakers        | 21,449                                      | Diverse speaker demographics                 |
| Utterance Length| Balanced distribution from 0 to 30 seconds   | Achieved via data appending                  |
| Text Source     | Various public domain and licensed sources   | Normalized and categorized                   |

## Pipeline Overview
1. **Data Conditioning**:
    - Audio Diarization (pyannote/speaker-diarization-3.1)
    - Text Categorizing (LNCat)
    - Text Normalization (N2gk+)
2. **Coreset Selection**:
    - Jamo Bigram (Grapheme level)
    - Dynamic UTMOS threshold (Audio quality level)
3. **Supplementary Finalization**:
    - Data Appending for duration balancing

## Dataset Usage
1. **Download**:
   - CoreaSpeech Dataset: [Hugging Face Link](https://huggingface.co/datasets/aanonyyy/F5I9N7A1)
   - Korean Universal Benchmark: [Hugging Face Link](https://huggingface.co/datasets/aanonyyy/M6A5P1Q7) 
2. **License**: CC BY-NC 4.0 (Details can be found with the dataset).
3. **Example Data Structure (Illustrative)**:
<!--
   ```
   /CoreaSpeech
     ├── speaker_id_00001
     │   ├── utterance_00001.wav
     │   └── utterance_00001.txt
     ├── speaker_id_00002
     │   ├── utterance_00002.wav
     │   └── utterance_00002.txt
     ...
   ```
-->

## Setup Steps (for using the pipeline/toolkit)
### 0. Environment Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/CoreaSpeech/CoreaSpeech.git # 실제 GitHub 링크로 교체
   cd CoreaSpeech
   ```
2. Create a Python virtual environment and install dependencies:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install -r requirements.txt # requirements.txt 파일 생성 필요
   ```

### 1. Configuration (if applicable)
Modify `config.yaml` (or similar) to set paths and parameters.
```yaml
# Example config.yaml snippet
raw_data_path: "/path/to/your/raw_korean_speech_data"
output_path: "/path/to/processed_coreaspeech_corpus"
utmos_threshold: 3.5 
# ... other parameters
```

### 2. Running the Pipeline Scripts
Execute the main script to process data:
```bash
python run_pipeline.py --config config.yaml
```
Or run individual stages:
```bash
python stage1_data_conditioning.py --input /raw/data --output /conditioned/data
python stage2_coreset_selection.py --input /conditioned/data --output /coreset/data
# ... etc.
```

### 3. Expected Output
- Processed audio files and transcripts in the specified output directory.
- Log files detailing the selection process and statistics.

## TODOs
* [X] Release initial CoreaSpeech dataset and benchmark.
* [X] Publish pipeline overview and usage instructions.
* [ ] Add more pre-trained models based on CoreaSpeech.
* [ ] Expand the benchmark with more diverse acoustic conditions.
* [ ] Develop an interactive demo for the TTS model.

## Acknowledgement
* This work utilizes or is inspired by:
    * Pyannote.audio for speaker diarization.
    * UTMOS for audio quality assessment.
    * Various open-source Korean NLP libraries.
* We thank all contributors and data providers.

---
*This README provides a general structure. Please fill in specific details, links, and code examples relevant to your project.* 