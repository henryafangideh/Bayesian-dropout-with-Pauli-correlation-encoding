# Qiskit Aer version

Open `pce_bayesian_dropout_aer.ipynb`. Its PCE training uses Aer statevector circuits; inference sampling uses Aer measurement counts in X, Y and Z bases. An additional density-matrix experiment uses an illustrative depolarizing and readout noise model.

Use Python 3.12 and install:

```sh
python -m pip install -r requirements-aer.txt
python -m pip install jupyterlab
python -m jupyterlab pce_bayesian_dropout_aer.ipynb
```

Run cells in order. No quantum account or hardware access is required. The noise model is not calibrated to a real device. The scientific limitations of the original prototype remain: fixed features, point-estimated readout, independent masks and three synthetic seeds. A simulator change does not establish improved inference or quantum advantage.

The notebook includes independent NumPy circuit checks, bit-ordering checks, parameter-shift validation, exact mask enumeration, grouped shot sampling and a comparison against exact noisy expectations. Code-cell execution is performed sequentially in a fresh Python process; the saved notebook is validated with `nbformat`. The package also retains the original NumPy notebook for comparison.

Files specific to this variant: `pce_bayesian_dropout_aer.ipynb`, `results_aer.json`, `predictions_aer.svg`, and `requirements-aer.txt`.

Official documentation: https://qiskit.github.io/qiskit-aer/tutorials/1_aersimulator.html and https://qiskit.github.io/qiskit-aer/tutorials/3_building_noise_models.html.
