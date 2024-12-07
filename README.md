
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

![Architecture Diagram](image.png)

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

