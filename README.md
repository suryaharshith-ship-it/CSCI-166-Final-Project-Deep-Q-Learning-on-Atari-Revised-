# Deep Q-Learning on Atari (Pong)

This project implements Deep Q-Learning on the Atari environment **ALE/Pong-v5** using PyTorch.
I trained **my own DQN baseline** and then implemented a **Double DQN (DDQN)** variant to compare their learning behavior.
The project follows the structure of the course starter notebook while adding my own experiments, learning curves, and gameplay videos.

---

## Project Overview

* **Environment:** ALE/Pong-v5
* **Frameworks:** PyTorch, Gymnasium, Stable Baselines 3 (wrappers)
* **Baseline agent:** My own DQN run (replay + target network)
* **Variant agent:** Double DQN (online-net action selection + target-net evaluation)
* **Outputs:** Learning curve plots + gameplay videos (early/random vs learned)

Both agents use identical preprocessing: grayscale frames, max-pooling, and **4-frame stacking**.

---


## Videos

| Description    | Link (add GitHub MP4 URL) |
| -------------- | ------------------------- |
| Early / Random | (https://github.com/suryaharshith-ship-it/CSCI-166-Final-Project-Deep-Q-Learning-on-Atari-Revised-/blob/main/videos/pong_ddqn_learned.mp4)           |
| DDQN Learned   | (https://github.com/suryaharshith-ship-it/CSCI-166-Final-Project-Deep-Q-Learning-on-Atari-Revised-/blob/main/videos/pong_early_random.mp4)

These videos demonstrate the agent’s behavior from the start of training (random) and after learning meaningful control using Double DQN.

---

## Learning Curve

I plotted the moving-average reward (last 100 episodes) for both of my runs:

* **My DQN baseline (~300k frames)**

  * Improves from ~–21 → ~–8.3
* **My Double DQN (~1.1M frames)**

  * Improves further to ~–6.3
  * Shows slightly more stable late-training behavior

The plot makes it clear that both agents learn, with DDQN outperforming the DQN baseline.

> You can find the plot here:
> (https://github.com/suryaharshith-ship-it/CSCI-166-Final-Project-Deep-Q-Learning-on-Atari-Revised-/blob/main/plots/plot.png)

---

## Hyperparameters

**Shared between DQN and DDQN:**

* **γ (discount):** 0.99
* **Optimizer:** Adam (learning rate = 1e-4)
* **Replay buffer:** 10,000
* **Replay start size:** 1,000
* **Batch size:** 32
* **Frame stack:** 4
* **Epsilon schedule:**

  * 1.0 → 0.01 linearly over 10,000 frames

**DDQN-specific:**

* **Target network sync:** every 500 frames
* **Double DQN update rule:**

  * Online network selects argmax action
  * Target network evaluates the Q-target

---

## Method Summary

1. Implemented a full DQN agent with convolutional architecture (Atari-style CNN).
2. Added Atari preprocessing, grayscale & resizing, and 4-frame stacking.
3. Implemented DDQN by modifying the TD target:

   * `argmax` from the **online** network
   * Q-value from the **target** network
4. Tracked learning with TensorBoard + manual logs.
5. Recorded two videos to show behavior improvement.

---

## Reflection

Pong is simple but still challenging due to sparse and delayed rewards.
To learn reliably, the agent needs enough exploration early on and stable Q-value updates later.
My DQN baseline showed steady improvement from completely losing to achieving ~–8.3 average score.

The Double DQN variant trained longer and consistently improved further, reaching ~–6.3. This matches DDQN’s goal of reducing overestimation bias and providing smoother learning.
The main issues I encountered were long training times and tuning epsilon decay.
With more time, I would try prioritized replay, N-step returns, and adjusting target-sync frequency for more stability.

---

## Starter Notebook Reference

This project was built on top of the provided starter file:

[`c166f25_02b_dqn_pong.ipynb`](ADD_LINK_HERE)

