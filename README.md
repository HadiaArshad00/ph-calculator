import math

def calculate_ph(h_conc):
    ph = -math.log10(h_conc)
    poh = 14 - ph
    oh_conc = 10 ** (-poh)
    return round(ph, 4), round(poh, 4), oh_conc

def classify(ph):
    if ph < 7:
        return "Acidic"
    elif ph == 7:
        return "Neutral"
    else:
        return "Basic"

print("=== pH Calculator ===")
print("Author: Hadia Arshad\n")

samples = [
    ("Stomach acid", 0.003162),
    ("Lemon juice",  0.003981),
    ("Coffee",       0.00001),
    ("Pure water",   0.0000001),
    ("Baking soda",  0.000000005),
]

for name, h_conc in samples:
    ph, poh, oh_conc = calculate_ph(h_conc)
    print(f"{name}")
    print(f"  pH  = {ph}  |  pOH = {poh}")
    print(f"  [H+] = {h_conc:.2e}  |  [OH-] = {oh_conc:.2e}")
    print(f"  Type: {classify(ph)}\n")
