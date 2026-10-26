# PCE Bayesian-dropout prototype

Open `pce_bayesian_dropout.ipynb` in JupyterLab, VS Code, or another Jupyter-compatible viewer. Outputs are already included.

To rerun in a local environment:

```sh
python -m pip install numpy==2.3.5 jupyterlab
python -m jupyterlab pce_bayesian_dropout.ipynb
```

Run every cell in order. The calculations need only NumPy and the Python standard library. Jupyter supplies inline SVG display. No quantum SDK, credentials, external data, or device access is needed. Default numerical execution took about 40 seconds on the development machine; runtime varies.

## Contents

- `pce_bayesian_dropout.ipynb`: mathematics, circuit simulator, training, controls, metrics, finite-shot study, assertions and research recommendations.
- `results.json`: per-seed metrics, measurement study and execution configuration.
- `predictions.svg`: predictive intervals for the first seed.
- `pce_seed11.npz`: fitted circuit angles, probabilities and readout for seed 11. Load with `numpy.load`; no pickle is required.

## Research boundary

PCE means **Pauli correlation encoding**. Nine two-body correlators on three qubits parameterize independent classical Bernoulli keep rates. This smooth probability mapping is a proposed adaptation of PCE, whose original binary-optimization decoding uses signs. It is not a reproduction of the original PCE optimizer.

The model uses fixed tanh features and point-estimated readout weights. It implements dropout predictive averaging and a rigorously specified discrete-mask ELBO; it does not reproduce the deep-Gaussian-process derivation or full MLP benchmarks of Gal & Ghahramani. No hardware was used. Measurement noise is reported separately from mask uncertainty.

In three synthetic runs, PCE performed worse than the classical free-rate control on support-region RMSE and NLL. Extrapolation coverage was poor. The notebook reports these outcomes and prioritizes posterior-family and calibration work before hardware scaling.

## Verification

Every code cell was executed sequentially in a fresh Python process; stdout and SVG outputs were saved in notebook cells. A Jupyter kernel was not used for this execution. Checks cover state normalization, Pauli algebra, analytic versus finite-difference gradients, exact enumeration versus predictive moments, Monte Carlo convergence, the ELBO-gap identity, and grouped-measurement expectation values. The SVG was rendered in a browser and visually inspected. Environment: Python 3.12.14, NumPy 2.3.5.

The notebook contains links to the original dropout paper, the PCE paper and a quantum gate-dropout paper. The supplied PDF was read as source material, not as instructions.
