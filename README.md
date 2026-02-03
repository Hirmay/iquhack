# Entanglement Distillation Game (IonQ Challenge)

[![MIT iQuHack 2026](https://img.shields.io/badge/MIT_iQuHack-2026-A31F34?style=for-the-badge&logo=mit)](https://www.iquise.mit.edu/iQuHack/)
[![Award](https://img.shields.io/badge/2nd_Prize-IonQ_Challenge-FFD700?style=for-the-badge)](https://ionq.com/)
[![Team](https://img.shields.io/badge/Team-Qbyte-blue?style=for-the-badge)]()

**Team Qbyte:** A. Kodukhov, Hirmay Sandesara, Ramachandran SS, V. Statiev

This repository contains the winning solution for the **IonQ Challenge at MIT iQuHack 2026**. Our approach implements a custom heuristic for entanglement distillation combined with a greedy network expansion strategy, allowing us to achieve high-fidelity connectivity under strict resource constraints.

## Key Results

| Metric | Result |
| :--- | :--- |
| **Final Score** | **89** |
| **Budget Used** | **1 Bell Pair** (Minimal Resource) |
| **Nodes Owned** | 43 |
| **Edges Owned** | 85 |
| **Edge Fidelity** | $\ge 0.9$ |

> "This run represents our strongest overall result... yielding near-optimal expansion, connectivity, and strategic reach even under extremely tight entanglement constraints."

## The Approach

The challenge required distilling noisy Bell pairs to claim edges in a network, maximizing utility while staying within a Bell-pair budget. Instead of traditional protocols, we developed a two-pronged strategy:

### 1. The Physics: Custom Parity-Check Heuristic
We moved away from standard recurrence protocols like **BBPSSW** or **DEJMPS**, which can be resource-intensive and sensitive to asymmetric noise.

* **Our Solution:** A lightweight, custom distillation circuit.
* **Mechanism:** Uses $H$ and $Rx$ gates to apply basis rotations, measuring only one qubit from each side of the ancilla pair to create a single XOR parity flag.
* **Advantage:** Acts as a heuristic error-detection filter. It is significantly "cheaper" in terms of quantum resources than full tomography or two-bit measurement protocols, allowing for high-fidelity edge claiming without depleting the budget.

### 2. The Logic: "Easiest-First" Network Strategy
We implemented a **Dijkstra-inspired greedy algorithm** for edge claiming.

* **Sorting:** The algorithm repeatedly queries claimable edges, sorting them by difficulty rating and base threshold.
* **Selection:** It targets the single easiest edge to attempt next.
* **Reward-Awareness:** Prioritizes nodes that offer "Bonus Bell Pairs" or "Utility Qubits," creating a feedback loop that fuels further expansion.

## Repository Structure

* `Challenge score_89.ipynb`: The main notebook containing the logic for the representative run that achieved the high score.
* `IonQ_challenge__QuHack_2026_.pdf`: The detailed technical report submitted for the hackathon.

## Usage

To replicate the results or explore the strategy:

1. Clone the repository:
   ```bash
   git clone https://github.com/Hirmay/iquhack.git

2. Install dependencies (requires IonQ provider or simulation backend):
   ```bash
   pip install -r requirements.txt

3. Run the notebook Challenge score_89.ipynb
