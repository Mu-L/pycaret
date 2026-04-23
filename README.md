<!-- =========================================================================
     PyCaret 4.0 is in active development. This banner updates visitors
     landing on the default (master, 3.4.0) branch. The 4.0 revamp lives on
     the `v4` branch. See also: https://github.com/pycaret/pycaret/tree/v4
     ========================================================================= -->

> ## 🛠 PyCaret 4.0 development has started — here's what's happening
>
> If you're here today, you're most likely on the **`master` branch (PyCaret 3.4.0)** — still installable via `pip install pycaret`, still works for existing 3.x code. But development has shifted: the **[4.0 revamp is live on the `v4` branch](https://github.com/pycaret/pycaret/tree/v4)** and we want to be transparent about what's going on.
>
> **Why.** PyCaret was released in 2020, widely adopted, and then went roughly three years without active maintenance. The consequences are real: it doesn't install cleanly on Python 3.12+, doesn't work with modern scikit-learn (≥1.5) or NumPy 2, and has 300+ open issues — many from people hitting exactly these compatibility cliffs. We owe you a maintained library.
>
> **What.** PyCaret 4.0 is a ground-up rebuild designed around how people actually use ML libraries in 2026:
>
> - **Sklearn-composable OOP engine.** `ClassificationExperiment`, `RegressionExperiment`, etc. are proper `sklearn.base.BaseEstimator` subclasses. `get_params`, `clone`, `__sklearn_tags__` all work.
> - **Lean.** Core dependencies cut from 30 → 19. Unmaintained integrations removed: mlflow, comet, wandb, dagshub, fugue, dask, ray, yellowbrick, gradio, fastapi, boto3, m2cgen, evidently, fairlearn. Full list at [`docs/revamp/KILL_LIST.md`](https://github.com/pycaret/pycaret/blob/v4/docs/revamp/KILL_LIST.md).
> - **Modern stack.** Works on Python 3.11 / 3.12 / 3.13, scikit-learn 1.7, NumPy 2, pandas 2.x. `uv` for environment management.
> - **Agent- and UI-native.** Typed dataclass returns from every verb (`CompareResult`, `TuneResult`, ...), a structured event stream (`pycaret.logging`), and JSON-serializable introspection (`pycaret.api`). The forthcoming open-source PyCaret React UI runs on this engine.
>
> **Current status (updated regularly):** ~22K lines of tech debt removed. 32/32 tests green on the new OOP surface across Python 3.11 / 3.12 / 3.13 × Ubuntu + Windows. Five canonical notebooks executing end-to-end. The 3.x god-class is being drained verb-by-verb; the public API is stable from here on.
>
> **Timeline.** No firm date — 4.0 ships when it's ready. First installable release will be `4.0.0alpha0` once the first three verbs are fully migrated off the legacy internals. Tracking in [`docs/revamp/ROADMAP.md`](https://github.com/pycaret/pycaret/blob/v4/docs/revamp/ROADMAP.md) and [`docs/revamp/STATUS.md`](https://github.com/pycaret/pycaret/blob/v4/docs/revamp/STATUS.md).
>
> **3.x will keep working** — no forced migration, no 3.x EOL date. If you don't want to move, don't. We're not going to break your existing code.
>
> **Try 4.0 today:**
>
> ```bash
> git clone -b v4 https://github.com/pycaret/pycaret.git
> cd pycaret
> uv sync --all-extras
> uv run pytest tests/                     # -> 32 passed
> uv run jupyter notebook notebooks/01_classification.ipynb
> ```
>
> **How this is being built.** PyCaret 4.0 is being built collaboratively with [Claude](https://www.anthropic.com/claude) (Anthropic's coding agent). Every non-trivial change, every architectural decision, and every trade-off is documented in [`docs/revamp/release_notes_pycaret4.md`](https://github.com/pycaret/pycaret/blob/v4/docs/revamp/release_notes_pycaret4.md) — commit-by-commit, session-by-session. The goal is both a better library and a reproducible case study of AI-assisted open-source revival.
>
> **Useful links on `v4`:**
> - [`README.md`](https://github.com/pycaret/pycaret/blob/v4/README.md) — 4.0 quickstart
> - [`AGENTS.md`](https://github.com/pycaret/pycaret/blob/v4/AGENTS.md) — instructions for AI contributors
> - [`docs/revamp/ARCHITECTURE.md`](https://github.com/pycaret/pycaret/blob/v4/docs/revamp/ARCHITECTURE.md) — the design
> - [`docs/revamp/KILL_LIST.md`](https://github.com/pycaret/pycaret/blob/v4/docs/revamp/KILL_LIST.md) — what was removed and why
> - [`docs/revamp/STATUS.md`](https://github.com/pycaret/pycaret/blob/v4/docs/revamp/STATUS.md) — current session status, refreshed every session
> - [`CONTRIBUTING.md`](https://github.com/pycaret/pycaret/blob/v4/CONTRIBUTING.md) — contributor guide for 4.0
>
> **Issues.** If you're hitting a compat cliff on 3.x (Python 3.12+, sklearn 1.5+, NumPy 2, pandas 2.2+), please **don't file new issues** — those are already fixed in 4.0. Try the `v4` branch instead.
>
> For everything else: 3.x README continues below.

---

<div align="center">

<img src="docs/images/logo.png" alt="drawing" width="200"/>

## **An open-source, low-code machine learning library in Python**
## 🎉🎉🎉 **PyCaret 3.4 is now available. 🎉🎉🎉**
## `pip install --upgrade pycaret` </br>

<p align="center">
<h3>
  <a href="https://pycaret.gitbook.io/">Docs</a> •
  <a href="https://pycaret.gitbook.io/docs/get-started/tutorials">Tutorials</a> •
  <a href="https://pycaret.gitbook.io/docs/learn-pycaret/official-blog">Blog</a> •
  <a href="https://www.linkedin.com/company/pycaret/">LinkedIn</a> •
  <a href="https://www.youtube.com/channel/UCxA1YTYJ9BEeo50lxyI_B3g">YouTube</a> •
    <a href="https://join.slack.com/t/pycaret/shared_invite/zt-row9phbm-BoJdEVPYnGf7_NxNBP307w">Slack</a>
</h3>
</p>

| Overview | |
|---|---|
| **CI/CD** | ![pytest on push](https://github.com/pycaret/pycaret/workflows/pytest%20on%20push/badge.svg) [![Documentation Status](https://readthedocs.org/projects/pip/badge/?version=stable)](http://pip.pypa.io/en/stable/?badge=stable) |
| **Code** |  [![!pypi](https://img.shields.io/pypi/v/pycaret?color=orange)](https://pypi.org/project/pycaret/) [![!python-versions](https://img.shields.io/badge/Python-3.9%20%7C%203.10%20%7C%203.11%20%7C%203.12-blue)](https://badge.fury.io/py/pycaret) [![!black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
| **Downloads**| [![Downloads](https://static.pepy.tech/personalized-badge/pycaret?period=week&units=international_system&left_color=grey&right_color=blue&left_text=weekly%20(pypi))](https://pepy.tech/project/pycaret) [![Downloads](https://static.pepy.tech/personalized-badge/pycaret?period=month&units=international_system&left_color=grey&right_color=blue&left_text=monthly%20(pypi))](https://pepy.tech/project/pycaret) [![Downloads](https://static.pepy.tech/personalized-badge/pycaret?period=total&units=international_system&left_color=grey&right_color=blue&left_text=cumulative%20(pypi))](https://pepy.tech/project/pycaret) |
| **License** | [![License](https://img.shields.io/pypi/l/ansicolortags.svg)](https://img.shields.io/pypi/l/ansicolortags.svg)
| **Community** | [![Slack](https://img.shields.io/badge/slack-chat-green.svg?logo=slack)](https://join.slack.com/t/pycaret/shared_invite/zt-20gl4zb8k-L~ZQDyi9LtrV4dWxYpLE7A) |



![alt text](docs/images/quick_start.gif)

<div align="left">

# Welcome to PyCaret
PyCaret is an open-source, low-code machine learning library in Python that automates machine learning workflows. It is an end-to-end machine learning and model management tool that speeds up the experiment cycle exponentially and makes you more productive.

In comparison with the other open-source machine learning libraries, PyCaret is an alternate low-code library that can be used to replace hundreds of lines of code with few lines only. This makes experiments exponentially fast and efficient. PyCaret is essentially a Python wrapper around several machine learning libraries and frameworks such as scikit-learn, XGBoost, LightGBM, CatBoost, Optuna, Hyperopt, Ray, and few more.

The design and simplicity of PyCaret are inspired by the emerging role of citizen data scientists, a term first used by Gartner. Citizen Data Scientists are power users who can perform both simple and moderately sophisticated analytical tasks that would previously have required more technical expertise. PyCaret was inspired by the caret library in R programming language.

# 🚀 Installation

## 🌐 Option 1: Install via PyPi
PyCaret is tested and supported on 64-bit systems with:
- Python 3.9, 3.10, 3.11 and 3.12
- Ubuntu 16.04 or later
- Windows 7 or later

You can install PyCaret with Python's pip package manager:

```python
# install pycaret
pip install pycaret
```

PyCaret's default installation will not install all the optional dependencies automatically. Depending on the use case, you may be interested in one or more extras:

```python
# install analysis extras
pip install pycaret[analysis]

# models extras
pip install pycaret[models]

# install tuner extras
pip install pycaret[tuner]

# install mlops extras
pip install pycaret[mlops]

# install parallel extras
pip install pycaret[parallel]

# install test extras
pip install pycaret[test]

# install dev extras
pip install pycaret[dev]

##

# install multiple extras together
pip install pycaret[analysis,models]
```

Check out all [optional dependencies](https://github.com/pycaret/pycaret/blob/master/requirements-optional.txt). If you want to install everything including all the optional dependencies:

```python
# install full version
pip install pycaret[full]
```
## 📄 Option 2: Build from Source
Install the development version of the library directly from the source. The API may be unstable. It is not recommended for production use.

```python
pip install git+https://github.com/pycaret/pycaret.git@master --upgrade
```

## 📦 Option 3: Docker
Docker creates virtual environments with containers that keep a PyCaret installation separate from the rest of the system. PyCaret docker comes pre-installed with a Jupyter notebook. It can share resources with its host machine (access directories, use the GPU, connect to the Internet, etc.). The PyCaret Docker images are always tested for the latest major releases.

```python
# default version
docker run -p 8888:8888 pycaret/slim

# full version
docker run -p 8888:8888 pycaret/full
```

## 🏃‍♂️ Quickstart

### 1. Functional API
```python
# Classification Functional API Example

# loading sample dataset
from pycaret.datasets import get_data
data = get_data('juice')

# init setup
from pycaret.classification import *
s = setup(data, target = 'Purchase', session_id = 123)

# model training and selection
best = compare_models()

# evaluate trained model
evaluate_model(best)

# predict on hold-out/test set
pred_holdout = predict_model(best)

# predict on new data
new_data = data.copy().drop('Purchase', axis = 1)
predictions = predict_model(best, data = new_data)

# save model
save_model(best, 'best_pipeline')
```

### 2. OOP API

```python
# Classification OOP API Example

# loading sample dataset
from pycaret.datasets import get_data
data = get_data('juice')

# init setup
from pycaret.classification import ClassificationExperiment
s = ClassificationExperiment()
s.setup(data, target = 'Purchase', session_id = 123)

# model training and selection
best = s.compare_models()

# evaluate trained model
s.evaluate_model(best)

# predict on hold-out/test set
pred_holdout = s.predict_model(best)

# predict on new data
new_data = data.copy().drop('Purchase', axis = 1)
predictions = s.predict_model(best, data = new_data)

# save model
s.save_model(best, 'best_pipeline')
```


## 📁 Modules
<div align="center">

## **Classification**

  Functional API           |  OOP API
:-------------------------:|:-------------------------:
![](docs/images/classification_functional.png)  | ![](docs/images/classification_OOP.png)

## **Regression**

  Functional API           |  OOP API
:-------------------------:|:-------------------------:
![](docs/images/regression_functional.png)  | ![](docs/images/regression_OOP.png)

## **Time Series**

  Functional API           |  OOP API
:-------------------------:|:-------------------------:
![](docs/images/time_series_functional.png)  | ![](docs/images/time_series_OOP.png)

## **Clustering**

  Functional API           |  OOP API
:-------------------------:|:-------------------------:
![](docs/images/clustering_functional.png)  | ![](docs/images/clustering_OOP.png)

## **Anomaly Detection**

  Functional API           |  OOP API
:-------------------------:|:-------------------------:
![](docs/images/anomaly_functional.png)  | ![](docs/images/anomaly_OOP.png)

<div align="left">

# 👥 Who should use PyCaret?
PyCaret is an open source library that anybody can use. In our view the ideal target audience of PyCaret is: <br />

- Experienced Data Scientists who want to increase productivity.
- Citizen Data Scientists who prefer a low code machine learning solution.
- Data Science Professionals who want to build rapid prototypes.
- Data Science and Machine Learning students and enthusiasts.

# 🎮 Training on GPUs
To train models on the GPU, simply pass use_gpu = True in the setup function. There is no change in the use of the API; however, in some cases, additional libraries have to be installed. The following models can be trained on GPUs:

- Extreme Gradient Boosting
- CatBoost
- Light Gradient Boosting Machine requires [GPU installation](https://lightgbm.readthedocs.io/en/latest/GPU-Tutorial.html)
- Logistic Regression, Ridge Classifier, Random Forest, K Neighbors Classifier, K Neighbors Regressor, Support Vector Machine, Linear Regression, Ridge Regression, Lasso Regression requires [cuML >= 0.15](https://github.com/rapidsai/cuml)

# 🖥️ PyCaret Intel sklearnex support
You can apply [Intel optimizations](https://github.com/intel/scikit-learn-intelex) for machine learning algorithms and speed up your workflow. To train models with Intel optimizations use `sklearnex` engine. There is no change in the use of the API, however, installation of Intel sklearnex is required:

```python
pip install scikit-learn-intelex
```

# 🤝 Contributors
<a href="https://github.com/pycaret/pycaret/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=pycaret/pycaret" width=600/>
</a>

# 📝 License
PyCaret is completely free and open-source and licensed under the [MIT](https://github.com/pycaret/pycaret/blob/master/LICENSE) license.

# ℹ️ More Information

| Important Links              |            Description                                       |
| -------------------------- | -------------------------------------------------------------- |
| :star: **[Tutorials]**        | Tutorials developed and maintained by core developers       |
| :clipboard: **[Example Notebooks]** | Example notebooks created by community               |
| :orange_book: **[Blog]** | Official blog by creator of PyCaret                      |
| :books: **[Documentation]**      | API docs                              |
| :tv: **[Videos]**            | Video resources             |
| ✈️ **[Cheat sheet]**            | Community Cheat sheet            |
| :loudspeaker: **[Discussions]**        | Community Discussion board on GitHub|
| :hammer_and_wrench: **[Release Notes]**          | Release Notes          |

[tutorials]: https://pycaret.gitbook.io/docs/get-started/tutorials
[Example notebooks]: https://github.com/pycaret/examples
[Blog]: https://pycaret.gitbook.io/docs/learn-pycaret/official-blog
[Documentation]: https://pycaret.gitbook.io/docs/
[Videos]: https://pycaret.gitbook.io/docs/learn-pycaret/videos
[Cheat sheet]: https://pycaret.gitbook.io/docs/learn-pycaret/cheat-sheet
[Discussions]: https://github.com/pycaret/pycaret/discussions
[Release Notes]: https://github.com/pycaret/pycaret/releases
