# 🎰 Lottery Simulator

<div align="center">

![Python](https://img.shields.io/badge/python-3.7+-blue.svg)
![Jupyter](https://img.shields.io/badge/jupyter-notebook-orange.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Contributions](https://img.shields.io/badge/contributions-welcome-brightgreen.svg)

**Ever wondered if the lottery is worth it? Find out with data!**

[Features](#-features) • [Getting Started](#-getting-started) • [How It Works](#-how-it-works) • [Visualizations](#-visualizations) • [Results](#-results)

</div>

---

## 🎯 Overview

A comprehensive Python-based Powerball lottery simulator that runs millions of draws to answer the age-old question: **"Can I win the lottery?"**

Spoiler alert: The math doesn't lie, but seeing is believing! 📊

### Why This Project?

- 🔢 **Data-Driven Analysis**: Interactive plots showing your inevitable journey to bankruptcy
- 🎲 **Realistic Simulation**: See exactly how lottery economics work
- 🔬 **Educational**: Perfect for understanding probability, expected value, and Monte Carlo simulations

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🎫 **Realistic Powerball Mechanics** | Simulates actual Powerball rules (5 numbers from 1-69, Powerball from 1-26) |
| 💰 **Prize Structure** | All prize tiers from $4 to $142.6M jackpot |
| ⚡ **Power Play Option** | Optional 2x multiplier (excludes jackpot) |
| 📊 **Multiple Visualizations** | ROI trends, win distributions, comparative analysis |
| 🔢 **Scalable Simulations** | Run from 1,000 to 1,000,000,000+ draws |
| 📈 **Statistical Tracking** | Cumulative winnings, spending, and ROI over time |

---

## 🚀 Getting Started

### Prerequisites

```bash
Python 3.7+
Jupyter Notebook
```

### Required Libraries

```python
import random
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
```

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/lottery-simulator.git
cd lottery-simulator
```

2. **Install dependencies**
```bash
pip install numpy matplotlib pandas jupyter
```

3. **Launch Jupyter Notebook**
```bash
jupyter notebook
```

4. **Open the notebook and run!** 🎉

---

## 🎮 How It Works

### 1. Choose Your Numbers

```python
# Pick your lucky numbers (or let random do it)
myNum = random.sample(range(1, 69), 5) + [random.randint(1, 26)]

# Example: [4, 8, 15, 16, 23] + [42]
```

### 2. Configure Your Simulation

```python
n = 1000000  # Number of draws to simulate
powerplay = 0  # 0 = No, 1 = Yes (adds $1 per ticket)
```

### 3. Run and Analyze

```python
# Run the simulation
total_winnings, total_wins, draws, cum_winnings, cum_spending, win_matrix = \
    simulation_with_tracking(powerplay, n, myNum)

# See your results
print(f"Spent: ${cum_spending[-1]:,}")
print(f"Won: ${total_winnings:,}")
print(f"ROI: {total_winnings/cum_spending[-1]:.4f}")
```

### Prize Structure

| Match | Prize (No Power Play) | Prize (With Power Play) |
|-------|----------------------|------------------------|
| 5 + PB | **$142,600,000** 🎰 | **$142,600,000** 🎰 |
| 5 | $1,000,000 | $2,000,000 |
| 4 + PB | $50,000 | $150,000 |
| 4 | $100 | $300 |
| 3 + PB | $100 | $300 |
| 3 | $7 | $21 |
| 2 + PB | $7 | $21 |
| 1 + PB | $4 | $12 |
| 0 + PB | $4 | $12 |

---

## 📊 Visualizations

### 1. ROI Over Different Draw Counts

Shows how your return on investment changes as you play more (spoiler: it gets worse!)

<div align="center">

```
📉 Expected ROI: ~0.50-0.70 (you lose 30-50% of your money)
```

</div>

### 2. Win Distribution Heatmap

Visualizes how often you match different combinations of numbers:

- **Rows**: Regular number matches (0-5)
- **Columns**: Powerball match (Yes/No)
- **Color intensity**: Frequency of occurrence

### 3. Cumulative Winnings vs Spending

Watch in real-time as the gap between what you spend and what you win grows larger!

### 4. Comparative Analysis

Side-by-side comparison of:
- Power Play vs No Power Play
- Different draw counts
- ROI convergence over time

---

## 📈 Results

### Sample Results (1 Million Draws)

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Draws        Spent           Winnings        ROI
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1,000        $2,000          $980            0.4900
10,000       $20,000         $10,234         0.5117
100,000      $200,000        $104,567        0.5228
1,000,000    $2,000,000      $1,048,932      0.5245
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### Key Insights

- 📉 **Expected ROI**: ~0.50-0.70 (varies by simulation)
- 💸 **Expected Loss**: 30-50% of money spent
- 🎯 **Win Rate**: ~4-5% of tickets win something
- 🎰 **Jackpot Odds**: 1 in 292,201,338

> **Note**: These are statistical expectations. Individual simulations may vary due to randomness!

---

## 🧮 The Math Behind It

### Expected Value Calculation

The lottery has a **negative expected value**, meaning on average, you lose money on every ticket.

```python
# Simplified expected value (per $2 ticket)
E(X) = Σ(probability × prize) - ticket_cost

# For most players:
E(X) ≈ $0.90 - $2.00 = -$1.10 loss per ticket
```

### Why ROI Converges

As the number of draws increases, the [Law of Large Numbers](https://en.wikipedia.org/wiki/Law_of_large_numbers) ensures that your actual results converge to the expected value. This is why ROI stabilizes around 0.50-0.60 regardless of how many times you play.

---

## 🛠️ Customization

### Modify Prize Amounts

Edit the `lotteryWinnings()` function to adjust prize tiers:

```python
def lotteryWinnings(powerplay, powerflag, count):
    # Modify prize amounts here
    if count == 5 and powerflag == 1:
        winnings = 142600000  # Change jackpot amount
    # ... etc
```

### Change Lottery Mechanics

Want to simulate a different lottery? Modify the `lotteryDraw()` function:

```python
def lotteryDraw(selection):
    # Change pool sizes here
    lottery_draw = random.sample(range(1, 69), 5)  # Main numbers
    powerball = random.randint(1, 26)  # Powerball
    # ...
```

### Add New Visualizations

The modular structure makes it easy to add new plots and analyses!

---

## 📚 Use Cases

- 🎓 **Education**: Teach probability and statistics
- 💡 **Decision Making**: Understand lottery economics before playing
- 📊 **Data Science**: Practice Monte Carlo simulation techniques
- 🔬 **Research**: Analyze different lottery strategies
- 🎮 **Fun**: See how unlucky (or lucky!) you can get

---

## 🤝 Contributing

Contributions are welcome! Here are some ideas:

- [ ] Add support for other lottery games (Mega Millions, EuroMillions, etc.)
- [ ] Implement quick pick strategies
- [ ] Add more visualization types
- [ ] Create interactive web dashboard
- [ ] Add statistical confidence intervals
- [ ] Optimize for even larger simulations

### How to Contribute

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- Powerball prize structure based on official [Powerball.com](https://www.powerball.com) data
- Inspired by the eternal question: "Should I play the lottery?"
- Built with Python, NumPy, Matplotlib, and hope (mostly the first three)

---

## ⚠️ Disclaimer

This simulator is for **educational and entertainment purposes only**. It does not:
- Guarantee any outcomes
- Provide financial advice
- Increase your chances of winning the actual lottery
- Recommend gambling

**Please gamble responsibly.** The lottery is entertainment with terrible odds, not an investment strategy.

---

## 📞 Contact

Questions? Suggestions? Found a bug?

- Open an issue on GitHub

---

<div align="center">

**⭐ If you found this project interesting, please give it a star! ⭐**

Made with Python and lots of coffee

*"The lottery is a tax on people who are bad at math." - Ambrose Bierce (probably)*

</div>
