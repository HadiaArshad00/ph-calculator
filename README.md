# pH Calculator in Python

A lightweight, modular script to calculate the pH of various chemical solutions including strong/weak acids and strong/weak bases.

## Features
-Strong Acid pH: Uses standard pH = -\log_{10}[H^+].
-Strong Base pH: Calculates via $pOH$ to derive pH.
-Weak Acid/Base pH: Utilizes the standard equilibrium approximations ([H^+] = \sqrt{K_a \cdot C} and [OH^-] = \sqrt{K_b \cdot C}).

## Usage
Simply clone the repository and run the script to see the built-in demo examples:
```bash
python ph_calculator.py
