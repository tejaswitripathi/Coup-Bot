# AI Bluff Bot 🤖🃏  
*An AI agent that plays the social deduction game **Coup** using reinforcement learning with dynamic opponent modeling.*

## 🎯 Goal  
To develop a powerful AI agent that learns and adapts optimal strategies to win **Coup** against static and dynamic opponents, using **Reinforcement Learning** techniques, especially Actor-Critic and RNNs.

## 🕹️ What is Coup?  
Coup is a hidden-role, bluff-heavy card game where each player starts with 2 influence cards and 2 coins. Players attempt to outmaneuver and eliminate others through strategic actions, deception, and deduction.  

Key elements include:
- Actions like **Income**, **Tax**, **Steal**, **Assassinate**, **Coup**, and **Exchange**
- Bluffing about influences (Duke, Captain, Assassin, etc.)
- Blocking and challenging moves
- Final goal: be the **last player standing**

## 🧠 Approach  
We modeled Coup as a reinforcement learning problem where:
- The **reward** is sparse: primarily based on winning or losing
- The **state** is sequential: the full game history matters
- The **opponents** use both static and dynamic strategies

### ✅ Key Design Choices:
- **Actor-Critic Algorithm**: Actor plays; Critic evaluates performance post hoc
- **RNN-based Architecture**: To retain and process game history
- **Intermediate Rewards**:
  - +0.5 for making opponent lose a card  
  - −2.5 for losing own card  
  - +0.05 × coins gained  
  - −0.05 × coins stolen from  
  - +10.0 for victory, −10.0 for loss
- **Opponent Strategy Modeling**:
  - Archetypes: *Greedy*, *Thief*, *Assassin*
  - Dynamic switching between strategies mid-game

## 🔍 Prior Research + Improvements  
We built upon earlier works (e.g. Stanford’s MCTS agent, Ryan Campbell’s Q-learning bot), addressing their limitations:
- Used **4 networks** (action, block, challenge, card selection) instead of 1  
- Incorporated **game history** using RNNs  
- Trained on **dynamic opponents** instead of static strategies  

## 📊 Results  
- Achieved **92.2% win rate** in 4-player environments  
- Defeated:
  - *Greedy* (99.9%)  
  - *Thief* (99.8%)  
  - *Assassin* (74.3%)  
- Strong performance against **dynamic strategy switching**  
- Demonstrated rational behavior: e.g., **reduced bluffing** under high risk

## 🔬 Analysis
- **Adequacy & Conservation**: The agent avoids unnecessary risks  
- **Rationality**: Prefers actions that maximize long-term survival  
- **Generalizability**: Performs well across various archetypes and conditions

## 🧪 Future Work  
- Train against **humans** or **self-play**  
- Compare against **standard RL benchmarks** (e.g., Atari agents)  
- Add **multi-agent interaction modeling** for more realism

## 💻 Requirements
- Python ≥ 3.8  
- PyTorch  
- NumPy, Matplotlib, tqdm, etc.

## ✍️ Author  
Tejaswi Tripathi  
📧 tt507@scarletmail.rutgers.edu
