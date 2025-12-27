 IIoT DDoS Detection with Deep Reinforcement Learning (Multi-Model, Multi-Dataset)

This repository contains the complete code, notebooks, models, and figures for the paper:

Real-Time DDoS Detection in Industrial IIoT Using Deep Reinforcement Learning: A Multi-Model, Multi-Dataset Evaluation**

The project evaluates five DRL agents (DQN, Double DQN, Duelling DQN, DDPG, PPO) on three benchmark datasets (KDDCup99, CIC-DDoS2019, Edge-IIoT) for binary DDoS detection. PPO emerges as the best performer with up to 99.3% accuracy and sub-0.12 ms inference latency.

Repository Structure

```
.
├── figures/                          # High-resolution figures (pipeline, confusion matrices, latency)
├── models/                           # Exported ONNX PPO models (one per dataset)
├── scalers/                          # RobustScaler objects (one per dataset)
├── notebook.ipynb                    # Main Jupyter notebook (full pipeline)
├── requirements.txt                  # Python dependencies
├── README.md                         # This file
└── data/                             # (Not included – datasets are public, see links below)
```

 Datasets (Public – Download Separately)

The three benchmark datasets are publicly available:

- KDD Cup 1999: http://kdd.ics.uci.edu/databases/kddcup99/kddcup99.html
- CIC-DDoS2019: https://www.unb.ca/cic/datasets/ddos-2019.html
- Edge-IIoTset: https://ieee-dataport.org/documents/edge-iiotset-new-comprehensive-realistic-cyber-security-dataset-iot-and-iiot-applications

Place them under `F:\jupyter\kagglehub` (or modify `base_path` in the notebook) using the exact folder structure specified in the code.

 Quick Start

1. Clone the repository
   ```bash
   git clone https://github.com/yourusername/multi-drl-iiot-ddos-detection.git
   cd multi-drl-iiot-ddos-detection
   ```

2. Create a virtual environment (recommended)
   ```bash
   python -m venv venv
   source venv/bin/activate    # Linux/macOS
   venv\Scripts\activate       # Windows
   ```

3. Install dependencies
   ```bash
   pip install -r requirements.txt
   ```

4. Run the notebook
   - Open `notebook.ipynb` in Jupyter
   - Execute all cells sequentially
   - The notebook will:
     - Load and preprocess all three datasets
     - Train all 5 DRL agents
     - Evaluate and generate figures/tables
     - Export PPO ONNX models and scalers

Reproducing Results

- All random seeds are fixed to 42 for full determinism
- The notebook has been tested on:
  - Python 3.11.5
  - PyTorch 2.1.0 (CPU)
  - Windows 11, Intel Core i7-11800H, 16 GB RAM

Expected outcomes:
- PPO achieves 99.3% on KDDCup99, 93.7% on CIC-DDoS2019, 95.5% on Edge-IIoT
- Inference latency < 0.12 ms per sample
- ONNX models saved in `models/`
- Figures saved in `figures/`

Real-Time Deployment

A lightweight real-time detector script (using only ONNX Runtime and NumPy) can be created from the exported models and scalers. No PyTorch required in production.

Citation

If you use this code or results, please cite:

```bibtex
Mikiyas Alemayehu, Mohamed Chahine Ghanem, Hamza Kheddar, Geetanjali Rathee, Chaker
Abdelaziz Kerrache
  year={2026}
}
```

License

MIT License – feel free to use, modify, and distribute.

Contact

For questions or access during review, contact the corresponding author.
