# ph-calculator
Python tool to calculate pH, pOH and ion concentrations
# =============================================
#   🧪 pH Calculator
#   Author: Hadia Arshad
#   Description: Calculate pH, pOH, [H+] and
#   [OH-] from user input
# =============================================

import math

def calculate_from_concentration(h_conc):
    if h_conc <= 0:
        return None, "Concentration must be greater than 0"
    ph = -math.log10(h_conc)
    poh = 14 - ph
    oh_conc = 10 ** (-poh)
    return {"pH": round(ph, 4),
            "pOH": round(poh, 4),
            "[H+]": f"{h_conc:.2e} mol/L",
            "[OH-]": f"{oh_conc:.2e} mol/L"}, None

def calculate_from_ph(ph):
    if ph < 0 or ph > 14:
        return None, "pH must be between 0 and 14"
    poh = 14 - ph
    h_conc = 10 ** (-ph)
    oh_conc = 10 ** (-poh)
    return {"pH": round(ph, 4),
            "pOH": round(poh, 4),
            "[H+]": f"{h_conc:.2e} mol/L",
            "[OH-]": f"{oh_conc:.2e} mol/L"}, None

def classify_solution(ph):
    if ph < 7:
        return f"Acidic 🔴 (pH {ph} < 7)"
    elif ph == 7:
        return "Neutral ⚪ (pH = 7)"
    else:
        return f"Basic/Alkaline 🔵 (pH {ph} > 7)"

def print_results(results, ph):
    print("\n  📊 Results:")
    print("  " + "-" * 35)
    for key, value in results.items():
        print(f"  {key:<8} = {value}")
    print(f"\n  🧪 Solution type: {classify_solution(ph)}")
    print()

def show_menu():
    print("\n" + "=" * 40)
    print("   🧪  pH Calculator")
    print("        Author: Hadia Arshad")
    print("=" * 40)
    print("  Commands:")
    print("  • 'ph'    → Enter a pH value")
    print("  • 'h'     → Enter [H+] concentration")
    print("  • 'ex'    → Show examples")
    print("  • 'quit'  → Exit")
    print("=" * 40 + "\n")

def show_examples():
    examples = [
        ("Stomach acid", 1.5),
        ("Lemon juice", 2.4),
        ("Coffee", 5.0),
        ("Pure water", 7.0),
        ("Baking soda", 8.3),
        ("Bleach", 12.5),
    ]
    print("\n  📋 Common pH Examples:")
    print("  " + "-" * 35)
    for name, ph in examples:
        classification = "Acidic" if ph < 7 else "Neutral" if ph == 7 else "Basic"
        print(f"  {name:<15} pH = {ph:<5} ({classification})")
    print()

# --- Main Program ---
show_menu()

while True:
    user_input = input("  Enter command: ").strip().lower()

    
    
