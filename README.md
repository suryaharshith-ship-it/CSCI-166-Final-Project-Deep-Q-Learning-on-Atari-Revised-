# 🎮 Deep Q-Learning on Atari (Pong)

This is my final project for the DQN Atari assignment.
I used Pong as my environment and built two agents:

1. **Baseline DQN** (from the starter notebook)
2. **Double DQN (DDQN)** as my required variant

My goal was to compare how the baseline learns vs. how the DDQN version works, and to show actual learning progress with curves and videos.

---

## 📌 Project Overview

* **Game:** ALE/Pong-v5
* **Frameworks:** PyTorch, Gymnasium, Stable Baselines 3 wrappers
* **Baseline:** Regular DQN with replay buffer + target network
* **Variant:** Double DQN (online argmax + target net evaluation)
* **Videos:** One early/random and one trained/DDQN

I followed the starter code and added the DDQN update myself.

---

## 📁 Repo Layout

```
/
├── notebooks/
│   ├── baseline_dqn_pong.ipynb      # Baseline DQN run (starter notebook)
│   └── ddqn_pong_variant.ipynb      # My DDQN version
│
├── videos/
│   ├── pong_early_random.mp4        # Random early behavior
│   └── pong_ddqn_learned.mp4        # Trained DDQN behavior
│
├── plots/
│   └── training_curve.png           # Baseline vs DDQN curve
│
└── README.md
```

---

## 🎥 Videos

Here are the two required videos showing the agent’s behavior:

| Video          | Link                            |
| -------------- | ------------------------------- |
| Early / Random | *(add link to the MP4 in repo)* |
| DDQN Learned   | *(add link to the MP4 in repo)* |

---

## 📈 Learning Curves

I plotted both:

* Baseline DQN (using the provided learning curve for now)
* My DDQN training run

The DDQN learns faster and reaches better reward compared to the baseline.

See the plot here:

```
plots/training_curve.png
```

---

## 🔧 Hyperparameters (important ones)

* **Discount (γ):** 0.99
* **Optimizer:** Adam, LR = 1e-4
* **Replay buffer:** 10,000
* **Batch size:** 32
* **Frame stack:** 4
* **Target sync:** 500 (for my DDQN run)
* **Epsilon:** 1.0 → 0.01 linear decay

---

## 🧪 Methods

* Baseline DQN: Ran the starter notebook as-is.
* DDQN: Modified the loss so the online net picks the best action and the target net evaluates it.
* Logged reward curves and compared performance.
* Recorded videos to show behavior before vs. after training.

---

## 📝 Reflection (Short Version)

Pong is simple but still tricky because rewards are sparse and the agent needs time to figure things out.
The baseline improved slowly, but the DDQN version clearly did better and had more stable updates.

The hardest parts were long training times and tuning epsilon decay.
If I had more time, I’d try things like prioritized replay, different target sync rates, or maybe N-step returns.

---

## 🔗 Starter Notebook Used

[`c166f25_02b_dqn_pong.ipynb`](ADD_LINK_HERE)
