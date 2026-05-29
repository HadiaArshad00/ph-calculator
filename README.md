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
import math

def calculate_ph_strong_acid(concentration: float) -> float:
    """Calculates the pH of a strong acid. Formula: pH = -log10([H+])"""
    if concentration <= 0:
        raise ValueError("Concentration must be greater than 0.")
    return -math.log10(concentration)

def calculate_ph_strong_base(concentration: float) -> float:
    """Calculates the pH of a strong base. Formula: pOH = -log10([OH-]), pH = 14 - pOH"""
    if concentration <= 0:
        raise ValueError("Concentration must be greater than 0.")
    poh = -math.log10(concentration)
    return 14 - poh

def calculate_ph_weak_acid(ka: float, concentration: float) -> float:
    """Calculates pH of a weak acid using standard approximation: [H+] = sqrt(Ka * C)"""
    if ka <= 0 or concentration <= 0:
        raise ValueError("Ka and concentration must be greater than 0.")
    h_concentration = math.sqrt(ka * concentration)
    return -math.log10(h_concentration)

def calculate_ph_weak_base(kb: float, concentration: float) -> float:
    """Calculates pH of a weak base using standard approximation: [OH-] = sqrt(Kb * C)"""
    if kb <= 0 or concentration <= 0:
        raise ValueError("Kb and concentration must be greater than 0.")
    oh_concentration = math.sqrt(kb * concentration)
    poh = -math.log10(oh_concentration)
    return 14 - poh

# --- Examples and Demonstration ---
if __name__ == "__main__":
    print("=== pH Calculator Examples ===")
    
    # Example: 0.01 M HCl
    print(f"Strong Acid (0.01 M): pH = {calculate_ph_strong_acid(0.01):.2f}")
    
    # Example: 0.001 M NaOH
    print(f"Strong Base (0.001 M): pH = {calculate_ph_strong_base(0.001):.2f}")
    
    # Example: 0.1 M Acetic Acid (Ka = 1.8e-5)
    print(f"Weak Acid (0.1 M, Ka=1.8e-5): pH = {calculate_ph_weak_acid(1.8e-5, 0.1):.2f}")
