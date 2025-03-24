# 🧭 MAGELLAN: Metacognitive predictions of learning progress guide autotelic LLM agents in large goal spaces

**MAGELLAN (MetAcognitive GEneralization of Learning progress in LANguage model agents)** is a metacognitive framework designed for Large Language Model (LLM) agents. It enables LLM agents to predict their competence and Learning Progress (LP) online, leveraging semantic relationships between goals to prioritize learning efficiently. By integrating MAGELLAN with online Reinforcement Learning (RL), agents can navigate vast goal spaces adaptively, ensuring efficient learning in high-dimensional and evolving goal spaces.

<div align=center>
  
![magellan (1)](https://github.com/user-attachments/assets/520b3117-829a-44b8-8b9b-72131187c177)

</div>

---

## 🛠 Installation

To set up MAGELLAN, you need to install the following dependencies:

- **[Lamorel](https://github.com/flowersteam/lamorel)**
- **[LittleZoo](https://github.com/flowersteam/littlezoo)**

Follow the installation instructions in the respective repositories.

---

## 🚀 Usage

### ⚙️ Configuration

MAGELLAN uses **Hydra** for configuration management. Example configurations can be found in the `configs/` directory.

### 🎯 Training

To train a model using different goal sampling strategies, run one of the following commands:

```bash
# Random goal sampling
python -m lamorel_launcher.launch --config-path configs/little_zoo/ --config-name local_gpu_config_random rl_script_args.path=magellan/main.py rl_script_args.output_dir=outputs/random rl_script_args.seed=0

# Online-ALP goal sampling
python -m lamorel_launcher.launch --config-path configs/little_zoo/ --config-name local_gpu_config_online rl_script_args.path=magellan/main.py rl_script_args.output_dir=outputs/online rl_script_args.seed=0

# EK-Online-ALP goal sampling
python -m lamorel_launcher.launch --config-path configs/little_zoo/ --config-name local_gpu_config_ek_online rl_script_args.path=magellan/main.py rl_script_args.output_dir=outputs/ek_online rl_script_args.seed=0

# MAGELLAN goal sampling
python -m lamorel_launcher.launch --config-path configs/little_zoo/ --config-name local_gpu_config_magellan rl_script_args.path=magellan/main.py rl_script_args.output_dir=outputs/magellan rl_script_args.seed=0
```

### 🔄 Resume Training

To resume training from a checkpoint:

```bash
python -m lamorel_launcher.launch --config-path configs/little_zoo/ --config-name local_gpu_config_magellan rl_script_args.path=magellan/main.py rl_script_args.output_dir=outputs/magellan rl_script_args.seed=0 rl_script_args.loading_path=outputs/magellan/10000
```

### 🖥️ HPC Cluster Usage

SLURM job scripts are available for training on HPC clusters:

```bash
# Submit a job with random goal sampling
sbatch configs/little_zoo/random.sl

# Submit a job with MAGELLAN goal sampling
sbatch configs/little_zoo/magellan.sl
```

---

## 📁 Project Structure

- **`magellan/`** – Main source code
  - `main.py` – Entry point for training
  - `environment.py` – Environment-related code
  - `goal_sampler.py` – Goal sampling strategies
  - `models.py` – LLM actor, critic, and LP estimator implementations
  - `updater.py` – SAC and MAGELLAN update logic
  - `initializer.py` – Model initialization utilities
  - `utils/` – Helper functions and utilities
- **`configs/`** – Configuration files for experiments
  - `little_zoo/` – Configurations for the LittleZoo environment

---

## 📖 Citation

If you find this work useful, please cite:

```bibtex
@article{gaven2025magellan,
  title={MAGELLAN: Metacognitive predictions of learning progress guide autotelic LLM agents in large goal spaces},
  author={Gaven, Loris and Carta, Thomas and Romac, Cl{\'e}ment and Colas, C{\'e}dric and Lamprier, Sylvain and Sigaud, Olivier and Oudeyer, Pierre-Yves},
  journal={arXiv preprint arXiv:2502.07709},
  year={2025}
}
```

---

## 🤝 Contribute

Contributions are welcome! Feel free to open an issue or submit a pull request on [GitHub](https://github.com/LorisGaven/MAGELLAN). 🚀

