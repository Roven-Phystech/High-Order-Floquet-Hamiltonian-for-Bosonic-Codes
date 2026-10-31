# High-Order Floquet Hamiltonian Engineering for Bosonic Codes

Numerical code and data for the paper

> Fan Luo, Yingdan Xu, and Lingzhen Guo,
> *High-Order Floquet Hamiltonian Engineering for Bosonic Codes*,
> Commun. Theor. Phys. (arXiv:XXXX.XXXXX)

The notebook constructs the **second-order correction drive** of Floquet Hamiltonian
engineering via the Fock-basis recursive scheme, applies it to the four-component cat-state
Hamiltonian ($q = 4$, $\lambda = 1/4$, $\gamma = 1/4$, $\alpha_0 = 1.198$ at the smallest
sweet spot), and reproduces the numerical results of the paper:

- drive harmonics and the 1st/2nd-order Floquet–Magnus terms $\hat H_F^{(1)}$, $\hat H_F^{(2)}$ (Eqs. (12)–(14));
- amplitude/phase profiles $|k f^{(r)}(k,\tau)|$, $\arg[k f^{(r)}(k,\tau)]$ of the drives $r = 0,1,2$ (Fig. 2);
- code-subspace fidelity $F(\beta)$ over one Floquet period for $\beta \in [10^{-3}, 1]$,
  giving the power-law infidelity scalings $\mathrm{IF} \propto \beta^4, \beta^6, \beta^8$
  for the zeroth-, first-, and second-order drives (Fig. 3).

## Files

| File | Description |
|---|---|
| `code for High-order.ipynb` | main notebook (all numerics and figures) |
| `HL_matrix.npy` | cached drive harmonics $H_l$ ($\lvert l\rvert \le 30$, Fock truncation $N_p = 16$) |
| `V1L_matrix.npy` | cached first-order drive harmonics |
| `FM_data.npy`, `FM2_data.npy` | fidelity data for the 0th/1st- and 2nd-order drives |

The `.npy` caches allow skipping the heaviest computations (harmonic generation and the
$\beta$-sweep) and going straight to the analysis/plotting cells.

## Usage

```bash
pip install -r requirements.txt   # numpy, scipy, matplotlib, mpmath, joblib, tqdm
jupyter notebook "code for High-order.ipynb"
```

Set the working directory in the second cell (`os.chdir(...)`) to where the `.npy` files
are stored, then run the cells in order. Heavy parts are parallelized with `joblib`.

