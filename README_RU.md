# PyTorch Poetry Boilerplate (CUDA + CPU)

Language: [English](README.md) | [Русский](README_RU.md)

Готовый boilerplate [`pyproject.toml`](https://python-poetry.org/docs/pyproject/) для **проектов нейронных сетей на базе PyTorch**, оптимизированные как для **локальной разработки**, так и для будущего **дистрибутива PyPI**.

---

## Файлы

- `pyproject-cuda128.toml` — устанавливает PyTorch с поддержкой **CUDA 12.8** из официального каталога PyTorch wheel.
- `pyproject-cpu.toml` — версия, работающая только на CPU** и использующая стандартные PyPI wheels.

> Оба файла предварительно настроены с параметром `package-mode = false` для **локальной работы** (не нужно структурировать код как пакет).

---

## Нужно изменить версию CUDA?

- Определите, какую версию CUDA поддерживает ваша видеокарта. Это можно сделать здесь: [Таблица совместимости CUDA](https://developer.nvidia.com/cuda-gpus)
- Убедитесь, что CUDA установлена ​​на вашем компьютере. Руководство: [CUDA Quick Start](https://docs.nvidia.com/cuda/cuda-quick-start-guide/index.html) | [Windows](https://docs.nvidia.com/cuda/cuda-installation-guide-microsoft-windows/) | [Linux](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/)
- В файле `pyproject-cuda128.toml` измените source `url = "https://download.pytorch.org/whl/cu128"` на вашу версию. Например, для CUDA версии 12.7 URL-адрес будет заканчиваться на `cu127`

## Быстрый старт

1. Выберите версию:
  ```bash
  # Для видеокарт NVIDIA (CUDA 12.8)
  cp pyproject-cuda128.toml pyproject.toml
  
  # ИЛИ только для CPU
  cp pyproject-cpu.toml pyproject.toml
  ```

2. Инициализируйте среду Poetry:
  ```bash
  poetry install
  ```

3. Запустите `poetry env activate`

4. Начните кодировать! Разметка `src/` или структура пакета не требуются.

---

## Хотите опубликовать на PyPi?

1. Установите `package-mode = true`
2. Раскомментируйте эту строку:
  ```bash
  # packages = [{ include = "your_package_name", from = "src" }]
  ```

3. Переместите код в `src/your_package_name/`
4. Убедитесь, что в вашем проекте есть корректный файл `__init__.py`
5. Запустите `poetry build` и `poetry publish`
> Сохраняйте `package-mode = false` во время исследования/создания прототипа. Устанавливайте `true` только при подготовке распространяемой библиотеки.

---

## Включенные зависимости
- `torch`, `torchaudio`, `torchvision` (CUDA или CPU)
- `tensorboard`
- `numpy`, `scikit-learn`
- `matplotlib`, `seaborn`
- `tqdm`

---

### Не нужны некоторые из включённых зависимостей?

Просто удалите их:
  ```bash
  poetry remove needed-dependency-name
  ```

## Лицензия

MIT — free to use, contribute, fork and copy.
