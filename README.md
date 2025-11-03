# Hangman using HMM + Reinforcement Learning

**REPO for Team 2, D Section**

## 👥 Students

1. **Rohann Rahul Shah (AM241)**
2. **Nikhilesh Venkat (AM192)**
3. **Nirav B (AM193)**

---

## 📘 Project Overview

This project combines a **Hidden Markov Model (HMM)** with **Reinforcement Learning (RL)** to build an intelligent Hangman-playing agent.
The HMM predicts likely letters based on learned letter transition and emission probabilities, while the RL agent (using Deep Q-Learning) learns to make optimal guesses over multiple games.

---

## 🧠 Core Algorithms

* **HMM (Hidden Markov Model):**
  Trained on a corpus of words to estimate state transitions and emission probabilities for different word lengths.
  Provides letter probabilities as hints to guide the RL agent.

* **QL (Q-Learning):**
  Learns optimal letter-guessing policies using states (masked word, guessed letters, lives, and HMM probabilities) and a reward system.
  Uses ε-greedy exploration with decay for balancing exploration and exploitation.

---

## ⚙️ Training Pipeline

1. **Train HMMOracle:**
   Learns statistical patterns from the word corpus.
2. **Train QL-HMM Agent:**
   The RL agent interacts with the Hangman environment to maximize rewards using HMM guidance.
3. **Evaluate Agent:**
   Tests the trained model on unseen words and reports accuracy, wrong guesses, and score.

---

## 🧩 Design Summary

* **State Representation:** Masked word + guessed letters + lives + HMM letter probabilities
* **Rewards:**

  * +20 correct letter
  * −2 wrong letter
  * −5 repeated guess
  * +100 win
  * −100 loss
* **Exploration:** ε-greedy strategy with decay, guided by HMM probabilities
* **Integration:** HMM outputs letter probabilities, which are fed into the RL state vector for better contextual awareness.

---

## 🚀 Future Improvements

* Adaptive weighting between HMM and RL predictions
* Better reward shaping and longer training
* Curriculum learning by word difficulty
* Adding LSTM-based sequence modeling to improve letter prediction

---

## 📂 File Structure

```
│── Data/
│   ├── corpus.txt
│   ├── test.txt
│
│── hangman_hmm_rl.py
│── hangman_hmm.pkl
│── README.md
```

---

## ▶️ How to Run

1. Place your training (`corpus.txt`) and test (`test.txt`) data in the `Data/` folder.
2. Run:

   ```bash
   python hangman_hmm_rl.py
   ```
3. The model will train the HMM, then the DQN agent, and finally evaluate on the test set.

---

## 🏁 Outcome

The trained agent learns to efficiently guess letters, balancing statistical insight from the HMM with learned reinforcement strategies for optimal performance in Hangman.

