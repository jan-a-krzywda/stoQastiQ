# **Quantum methods for generating stochastic trajectories:** key directions and tools

Stochastic trajectory generation on quantum hardware can be approached via quantum reservoir computing, variational/parametric circuits for SDEs, and hybrid quantum–classical generative models. Existing work mainly shows **principled speedups** or **expressivity gains**, with early demonstrations on superconducting and annealing devices, including pulse-level control.

## Quantum advantage for stochastic processes and SDEs

**Algorithmic speedups**

- Quantum multilevel Monte Carlo for SDEs gives a **quadratic speed-up** in precision over classical Monte Carlo for expectations in finance models such as Black–Scholes and local volatility  (An et al., 2020).
- A variational quantum algorithm embeds SDE probability distributions directly in amplitudes and simulates time evolution via a trinomial tree, aiming at efficient expectation-value evaluation for general SDEs <paper_cite paper_id="2e81e43fddaf553ea9487dff2d11b207" quote="we propose a quantum-classical hybrid algorithm that solves SDEs based on variational quantum simulation (VQS).""/>.
- Quantum quantile mechanics represents SDE solutions via **differentiable quantum circuits** implementing the quantile function, enabling time-series generation (e.g., Ornstein–Uhlenbeck) from time-propagated quantiles  (Paine et al., 2021).

- A general framework for continuous-time stochastic processes claims **exponential reductions** in space/time for encoding and quadratic speedups for information extraction, with finance examples such as Merton jump diffusion and ruin probabilities  (Zhuang et al., 2022).

## Quantum reservoir computing & noisy superconducting devices

**Using noise and measurements as a resource**

- Single-shot quantum reservoir computing is designed to use **structured noise** of few-qubit devices to generate trajectories of classical stochastic processes (including 1/f and Ornstein–Uhlenbeck noise) by learning linear maps from single-shot bitstring trajectories to target stochastic time series  (Van Nieuwenburg, 2025).
- Natural quantum reservoir computing uses **real superconducting quantum devices** as reservoirs, exploiting native dissipation/noise and showing improved performance over linear models on time-series regression and temporal classification  (Suzuki et al., 2021).
- Feedback-driven QRC restores memory lost by projective measurements by feeding outcomes back into the reservoir; it shows fading-memory behavior and good forecasting of quantum spin time series  (Kobayashi et al., 2024).
- Time-series QRC with weak vs projective measurements identifies protocols where **online weak measurements** achieve good memory and forecasting while keeping quantum advantage  (Mujal et al., 2022).
- Noise-engineered quantum reservoirs tune noise models within circuits to generate expressive nonlinear signals, achieving strong performance on chaotic benchmarks like Mackey–Glass  (Fry et al., 2023).

## Hybrid VAEs and quantum generative models

**Quantum-enhanced VAEs / RBMs / GANs**

- A **quantum variational autoencoder (QVAE)** uses a quantum Boltzmann machine in the latent space, with sampling performed on a D-Wave annealer; quantum-assisted training on MNIST shows competitive generative performance and suggests potential advantage when latent RBMs become large and classically hard to sample  (Winci et al., 2019).
- A discrete VAE with an RBM latent layer small enough for a D-Wave annealer generated thousands of chemically valid, drug-like molecules, illustrating a **hybrid generative pipeline** and a route to future QVAEs with genuine QBMs  (Gircha et al., 2021).
- Quantum-enhanced VAEs using a quantum latent layer (QeVAE) achieve more than 2× fidelity improvements over classical VAEs on hard quantum state distributions while using only a linear number of parameters, pointing to **expressivity gains** relevant for complex stochastic trajectories  (Rao et al., 2023).
- To combat mode collapse in quantum GANs, VAE-QWGAN fuses a classical VAE decoder with a hybrid quantum Wasserstein GAN and uses data-dependent latent sampling plus a learned Gaussian mixture prior, significantly improving diversity and quality of generated images  (Thomas et al., 2024).

## Circuit-based vs pulse-based superconducting implementations

**Parameterized circuits and hardware-efficient control**

- Parameterized quantum circuits (PQCs) act as general ML models capable of highly non-trivial and potentially classically intractable distributions even at low depth, supporting both **generative modeling** and supervised tasks on NISQ hardware  (Benedetti et al., 2019).
- Quantum circuit learning formalizes a hybrid scheme where low-depth circuits with tunable parameters approximate nonlinear functions, optimized iteratively by a classical outer loop  (Mitarai et al., 2018).
- Pulse-efficient transpilation for PQC-based quantum ML on superconducting hardware significantly **reduces circuit durations** and improves classification accuracy, also delaying barren plateaus in variational ansätze  (Melo et al., 2022).
- End-to-end learning directly in the **control-pulse space** on a superconducting processor (without explicit circuit compilation) achieves high accuracy on MNIST digits, showing that gate-free pulse parameterization is practical and can fully exploit limited resources  (Pan et al., 2022).
- Natural QRC already uses existing superconducting processors as reservoirs without heavy gate design, suggesting a near-term path from circuit-based experiments to **pulse-level-tuned reservoirs** on the same hardware  (Suzuki et al., 2021).

### Different approaches to stochastic trajectory generation

| Approach | Key idea | Hardware angle | Citations |
|---------|---------|----------------|-----------|
| Quantum multilevel MC for SDEs | Amplitude-estimation speedup for expectations | Gate-based, circuit model |  (An et al., 2020)|
| VQS / quantile / continuous-time frameworks | Variational circuits encode full probability/quantile evolution | NISQ PQCs; differentiable circuits |  (Kubo et al., 2020; Paine et al., 2021; Zhuang et al., 2022)|
| Quantum reservoir computing | Use device dynamics/noise as reservoir; learn linear readout for trajectories | Few-qubit, noisy superconducting or spin systems |  (Van Nieuwenburg, 2025; Suzuki et al., 2021; Mujal et al., 2022)|

**Figure 1:** Comparison of main quantum approaches for stochastic trajectories

## Finance-specific overviews and Monte Carlo links

- A broad review of quantum computing for finance surveys algorithms for **stochastic modelling, optimization and ML**, noting quadratic speedups for quantum Monte Carlo and challenges in resource requirements for real advantage  (Herman et al., 2023).
- A tutorial links Grover/amplitude estimation to **Monte Carlo integration** with Qiskit implementations in finance, and discusses scaling challenges for quantum simulation techniques  (Blanchet et al., 2025).

## Summary

Research provides several complementary routes for your project: (1) **algorithmic SDE approaches** (multilevel Monte Carlo, VQS, quantile mechanics, continuous-time frameworks) to generate and sample from stochastic trajectories; (2) **quantum reservoir computing**, particularly single-shot and natural superconducting reservoirs, to harness device noise and measurement for time-series generation; and (3) **hybrid generative models** (QVAE, DVAE+RBM, QeVAE, VAE-QWGAN) as blueprints for quantum–classical VAEs on future hardware. For circuit-based access, PQCs and quantum circuit learning give a generic modeling layer, while pulse-efficient and end-to-end pulse learning on superconducting processors demonstrate how to transition to **pulse-level, hardware-native generative models** as your device access evolves.
 
_These search results were found and analyzed using Consensus, an AI-powered search engine for research. Try it at https://consensus.app. © 2026 Consensus NLP, Inc. Personal, non-commercial use only; redistribution requires copyright holders’ consent._
 
## References
 
An, D., Linden, N., Liu, J.-P., Montanaro, A., Shao, C., & Wang, J. (2020). Quantum-accelerated multilevel Monte Carlo methods for stochastic differential equations in mathematical finance. *Quantum, 5*, 481. https://doi.org/10.22331/q-2021-06-24-481
 
Benedetti, M., Lloyd, E., Sack, S. H., & Fiorentini, M. (2019). Parameterized quantum circuits as machine learning models. *Quantum Science and Technology, 4*. https://doi.org/10.1088/2058-9565/ab4eb5
 
Blanchet, J. H., Squillante, M., Szegedy, M., & Wang, G. (2025). Connecting Quantum Computing with Classical Stochastic Simulation. *2025 Winter Simulation Conference (WSC)*, 58-72. https://doi.org/10.1109/wsc68292.2025.11339097
 
Fry, D., Deshmukh, A., Chen, S. Y.-C., Rastunkov, V., & Markov, V. (2023). Optimizing quantum noise-induced reservoir computing for nonlinear and chaotic time series prediction. *Scientific Reports, 13*. https://doi.org/10.1038/s41598-023-45015-4
 
Gircha, A. I., Boev, A. S., Avchaciov, K., Fedichev, P., & Fedorov, A. (2021). Hybrid quantum-classical machine learning for generative chemistry and drug design. *Scientific Reports, 13*. https://doi.org/10.1038/s41598-023-32703-4
 
Herman, D., Googin, C., Liu, X., Sun, Y., Galda, A., Safro, I., Pistoia, M., & Alexeev, Y. (2023). Quantum computing for finance. *Nature Reviews Physics, 5*, 450-465. https://doi.org/10.1038/s42254-023-00603-1
 
Kobayashi, K., Fujii, K., & Yamamoto, N. (2024). Feedback-Driven Quantum Reservoir Computing for Time-Series Analysis. *PRX Quantum*. https://doi.org/10.1103/prxquantum.5.040325
 
Kubo, K., Nakagawa, Y. O., Endo, S., & Nagayama, S. (2020). Variational quantum simulations of stochastic differential equations. *Physical Review A, 103*. https://doi.org/10.1103/physreva.103.052425
 
Melo, A., Earnest-Noble, N., & Tacchino, F. (2022). Pulse-efficient quantum machine learning. *Quantum, 7*, 1130. https://doi.org/10.22331/q-2023-10-09-1130
 
Mitarai, K., Negoro, M., Kitagawa, M., & Fujii, K. (2018). Quantum circuit learning. *Physical Review A*. https://doi.org/10.1103/physreva.98.032309
 
Mujal, P., Martínez-Peña, R., Giorgi, G., Soriano, M. C., & Zambrini, R. (2022). Time-series quantum reservoir computing with weak and projective measurements. *npj Quantum Information, 9*, 1-10. https://doi.org/10.1038/s41534-023-00682-z
 
Paine, A. E., Elfving, V., & Kyriienko, O. (2021). Quantum Quantile Mechanics: Solving Stochastic Differential Equations for Generating Time‐Series. *Advanced Quantum Technologies, 6*. https://doi.org/10.1002/qute.202300065
 
Pan, X., Cao, X., Wang, W., Cai, W., Li, X., Wang, H., Hu, J., Song, Y., Deng, D., Zou, C.-L., Wu, R., & Sun, L. (2022). Experimental quantum end-to-end learning on a superconducting processor. *npj Quantum Information, 9*, 1-6. https://doi.org/10.1038/s41534-023-00685-w
 
Rao, A., Madan, D., Ray, A., Vinayagamurthy, D., & M. S. S. (2023). Learning hard distributions with quantum-enhanced Variational Autoencoders.
 
Suzuki, Y., Gao, Q., Pradel, K., Yasuoka, K., & Yamamoto, N. (2021). Natural quantum reservoir computing for temporal information processing. *Scientific Reports, 12*. https://doi.org/10.1038/s41598-022-05061-w
 
Thomas, A., Youel, H., & Jose, S. T. (2024). VAE-QWGAN: addressing mode collapse in quantum GANs via autoencoding priors. *Quantum Machine Intelligence, 7*. https://doi.org/10.1007/s42484-025-00314-z
  
Winci, W., Buffoni, L., Sadeghi, H., Khoshaman, A., Andriyash, E., & Amin, M. H. (2019). A path towards quantum advantage in training deep generative models with quantum annealers. *Machine Learning: Science and Technology, 1*. https://doi.org/10.1088/2632-2153/aba220
 
Zhuang, X.-N., Chen, Z.-Y., Xue, C., Wu, Y., & Guo, G. (2022). Quantum Encoding and Analysis on Continuous Time Stochastic Process with Financial Applications. *Quantum, 7*, 1127. https://doi.org/10.22331/q-2023-10-03-1127
 
