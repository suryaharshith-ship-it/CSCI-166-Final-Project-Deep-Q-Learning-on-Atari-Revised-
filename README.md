Deep Q-Learning on Atari (Pong)

This project is my final assignment for Deep Q-Learning. I used the Pong environment (ALE/Pong-v5) and trained two agents:

1. Baseline DQN – from the starter notebook
2. Double DQN (DDQN) – my own modified version

The main goal was to compare how the regular DQN learns versus the Double DQN version, plot the results, record videos, and write up what worked and what didn’t.

---

Repository Structure

notebooks/

* baseline_dqn_pong.ipynb
* ddqn_pong_variant.ipynb

videos/

* pong_early_random.mp4
* pong_ddqn_learned.mp4

plots/

* training_curve.png

README.md

---

Videos

Early or random gameplay video:
(add link to pong_early_random.mp4 here)

DDQN learned gameplay video:
(add link to pong_ddqn_learned.mp4 here)

These two videos show the agent at the start and after training.

---

Learning Curves

I plotted both:

* The baseline DQN curve (from the starter notebook for now)
* My Double DQN training curve

The Double DQN learns faster and reaches better performance.

The curve image is located in:
plots/training_curve.png

---

Important Hyperparameters

Gamma: 0.99
Learning rate: 1e-4
Optimizer: Adam
Replay buffer size: 10000
Batch size: 32
Frame stack: 4
Target network sync: 500
Epsilon schedule: 1.0 down to 0.01

---

What I Did

* Ran the starter notebook to get the baseline DQN results
* Modified the loss function to implement Double DQN
* Trained the DDQN agent on Pong
* Logged the rewards and created the learning curves
* Recorded the early and learned video clips
* Prepared the comparison and wrote reflections

---

Short Reflection

I picked Pong because it is simple to understand but still tricky for reinforcement learning because rewards are sparse. The baseline DQN did learn slowly, but the Double DQN worked better and improved more.

Training time and getting epsilon decay right were the biggest challenges. If I had more time, I would try prioritized replay, different target sync intervals, or N-step returns.

---

Starter Notebook Used

c166f25_02b_dqn_pong.ipynb

