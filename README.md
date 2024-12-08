
# Bailando: AI-Driven 3D Dance Generation

## Overview
**Bailando** is a cutting-edge AI framework designed to generate synchronized 3D dance sequences. It combines the power of an Actor-Critic Generative Pre-trained Transformer (GPT) and a Choreographic Memory to address the challenges of spatial coherence and temporal alignment in dance choreography. This project bridges the gap between technology and creative arts, making it applicable in entertainment, virtual reality, and education.

---

## Features
- **Music-Driven Dance Generation**: Produces synchronized dance movements based on input music features like rhythm and tempo.
- **Actor-Critic GPT**: Ensures accurate posture predictions and movement optimization using reinforcement learning.
- **Choreographic Memory**: Encodes reusable upper and lower body movements for realistic choreography.
- **Full-Body 3D Sequences**: Outputs complete, rhythmically aligned dance routines.
- **Scalable and Future-Ready**: Supports API improvements and .fbx file format integration.

---

## Architecture
The Bailando architecture is composed of:
1. **Music Features Extraction**: Analyzes input music for rhythm, tempo, and emotional tone.
2. **Actor-Critic Motion GPT**: Predicts pose codes based on starting pose and music features.
3. **Choreographic Memory**: References pre-learned dance movements for realistic output.
4. **CNN Decoders**: Converts quantized pose codes into full-body 3D dance movements.



---

## Installation
### Prerequisites
- Python 3.8 or higher
- PyTorch
- Librosa (for music feature extraction)
- Windows Subsystem for Linux (WSL2) or Linux-based system
- CUDA Toolkit (if GPU support is required)

### Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/bailando.git
   ```
2. Navigate to the project directory:
   ```bash
   cd bailando
   ```
3. Install required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

---
## Data Preparation
In our experiments, we use AIST++ for evaluation. Please visit [here](https://google.github.io/aistplusplus_dataset/download.html) to download the AIST++ annotations and unzip them as './aist_plusplus_final/' folder, visit [here](https://aistdancedb.ongaaccel.jp/database_download/) to download all original music pieces (wav) into './aist_plusplus_final/all_musics'. And please set up the AIST++ API from [here](https://github.com/google/aistplusplus_api) and download the required SMPL models from [here](https://smpl.is.tue.mpg.de/). Please make a folder './smpl' and copy the downloaded 'male' SMPL model (with '_m' in name) to 'smpl/SMPL_MALE.pkl' and To download the preprocessed models download from [here](https://drive.google.com/file/d/1EGJeBE1fE59ByjxR_-ipwV6Dz-Cx-stT/view?usp=sharing) as ./data folder if you don't wish to process the data.

---
## Evaluation
To test with the pretrained models, please download the weights from [here](https://drive.google.com/file/d/1Fi0TIiBV6EQAQrBU0IOnlke2Nu4IcutC/view?usp=sharing) (Google Drive) or separately downloads the four weights from [[weight 1]](https://www.jianguoyun.com/p/DcicSkIQ6OS4CRiH8LYE)|[[weight 2]](https://www.jianguoyun.com/p/DTi-B1wQ6OS4CRjonbwEIAA)|[[weight 3]](https://www.jianguoyun.com/p/Dde220EQ6OS4CRiD8LYE)|[[weight4]](https://www.jianguoyun.com/p/DRHA80cQ6OS4CRiC8LYE) (坚果云) into ./experiments folder.

### 1. Generate dancing results

To test the VQ-VAE (with or without global shift as you indicated in config):

    sh srun.sh configs/sep_vqvae.yaml eval [your node name] 1

To test GPT:

    sh srun_gpt_all.sh configs/cc_motion_gpt.yaml eval [your node name] 1
   
To test final restuls:
    
    sh srun_actor_critic.sh configs/actor_critic.yaml eval [your node name] 1

### 2. Dance quality evaluations

After generating the dance in the above step, run the following codes.

### Step 1: Extract the (kinetic & manual) features of all AIST++ motions (ONLY do it by once):
    
    python extract_aist_features.py


### Step 2: compute the evaluation metrics:

    python utils/metrics_new.py

It will show exactly the same values reported in the paper. To fasten the computation, comment Line 184 of utils/metrics_new.py after computed the ground-truth feature once. To test another folder, change Line 182 to your destination, or kindly modify this code to a "non hard version" :)

1. To run the vis_pkl.py file:
   ```bash
   python vis_pkl.py
   ```
This runs a sample file and generates the output

## Usage
### Input
- Music file (e.g., .mp3 or .wav)
- Initial pose configuration (pose codes)

### Running the Framework
```bash
python bailando.py --input <music_file> --output <output_directory>
```

### Output
- 3D Dance Sequence in SMPL format
- API endpoints for further integration

---

## Challenges Addressed
- **Library Compatibility**: Transitioned to WSL2 for stable development.
- **GPU Limitations**: Resolved CUDA issues by shifting to CPU processing.
- **Data Handling**: Implemented logic to bypass corrupted files.
- **Partial Output Debugging**: Adjusted dimensions for full-body movement generation.

---

## Future Plans
- Transition to .fbx file formats for richer 3D data representation.
- Expand into virtual reality and gaming platforms.
- Incorporate emotional expressions into dance sequences.

---

## Contributing
We welcome contributions! To get started:
1. Fork the repository.
2. Create a feature branch.
3. Submit a pull request with a detailed description.

---

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

---

## Contact
For questions or feedback, please reach out to:
- **Email**: your-email@example.com
- **GitHub**: [your-username](https://github.com/your-username)

---

## Acknowledgments
- Teaching Assistants for their guidance on CUDA and debugging.
- Open-source contributors for tools like PyTorch and Librosa.

