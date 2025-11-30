# PyTorch Poetry Boilerplate (CUDA + CPU)

Language: [English](README.md) | [Русский](README_RU.md)

Ready-to-use [`pyproject.toml`](https://python-poetry.org/docs/pyproject/) templates for **PyTorch-based neural network projects**, optimized for both **local development** and future **PyPI distribution**.

---

## Files

- `pyproject-cuda128.toml` — installs PyTorch with **CUDA 12.8** support from the official PyTorch wheel index.
- `pyproject-cpu.toml` — pure **CPU-only** version using standard PyPI wheels.

> Both files are pre-configured with `package-mode = false` for **local experimentation** (no need to structure your code as a package).

---

## Need to change CUDA version?

- Define which version of CUDA your GPU supports. You can do it here: [CUDA Compability Table](https://developer.nvidia.com/cuda-gpus)
- Make sure that CUDA installed on your PC. Guide: [CUDA Quick Start](https://docs.nvidia.com/cuda/cuda-quick-start-guide/index.html) | [Windows](https://docs.nvidia.com/cuda/cuda-installation-guide-microsoft-windows/) | [Linux](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/)
- In `pyproject-cuda128.toml` change source  `url = "https://download.pytorch.org/whl/cu128"` to your version. For example, for CUDA v. 12.7 the end of url will be `cu127`

## Quick Start

1. Choose your version:
   ```bash
   # For NVIDIA GPU (CUDA 12.8)
   cp pyproject-cuda128.toml pyproject.toml

   # OR for CPU-only
   cp pyproject-cpu.toml pyproject.toml

2. Initialize Poetry environment:
  ```bash
  poetry install
  ```

3. Run `poetry env activate` 

4. Start coding! No `src/` layout or package structure required

---

## Want publish to PyPi Later?

1. Set `package-mode = true`
2. Uncomment this line:
  ```bash
  # packages = [{ include = "your_package_name", from = "src" }]
  ```

3. Move your code into `src/your_package_name/`
4. Ensure your project has a valid `__init__.py`
5. Run `poetry build` and `poetry publish`
> Keep `package-mode = false` during research/prototyping. Switch to `true` only when preparing a distributable library

---

## Included Dependencies
- `torch`, `torchaudio`, `torchvision` (CUDA or CPU)
- `tensorboard`
- `numpy`, `scikit-learn`
- `matplotlib`, `seaborn`, `pandas`
- `tqdm`, `pyyaml`

---

### Don't need some of included dependencies?

Just remove it:
  ```bash
  poetry remove unnecessary-dependency-name
  ```

## License

MIT — feel free to fork, modify, and use in your projects.
