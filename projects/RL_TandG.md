---
layout: project
type: project
image: img/TigerAndGoats_img/TandG_PortalPic.jpg
title: "Automatic Strategy Inference for Games"
date: 2023-11-30
published: true
labels:
  - Reinforcement Learning
  - Weather Prediction
  - Python
  - Power Forecasting
  - Automatic Strategy Inference
  - Games
summary: "Project explores the use of reinforcement learning (RL) for strategic decision-making in both games and forecasting tasks. Using the OpenSpiel API, RL agents were trained to play the Huligutta (Goats and Tigers) board game, against fixed Tiger strategies through value iteration methods. The approach was then extended to real-world problems, including adaptive weather prediction and net energy demand forecasting."
---

## Intro

<div style="text-align: center; margin-top: 20px;">
  <img src="../img/TigerAndGoats_img/Game.png" alt="In Game view of Tigers and Goats." style="max-width: 100%; height: auto; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
  <p style="font-size: 0.9em; color: black;">In Game view of Tigers and Goats.</p>
</div>
Reinforcement learning (RL) is transforming how machines make decisions, driving innovation in everything from game-playing AIs to autonomous vehicles and energy forecasting. To explore its potential, we began with a classic board game, Huligutta (Goats and Tigers)—a simple yet strategically rich environment. Its clear rules and asymmetric gameplay made it an ideal testbed for developing and evaluating RL models in a controlled setting.

After training an agent that achieved a 95% win rate against fixed strategies, we expanded our focus to more complex and unpredictable challenges: forecasting weather patterns and net energy demand. These real-world problems demand models that can adapt to noisy data, changing conditions, and incomplete information—precisely the scenarios where RL can shine. Leveraging the OpenSpiel API, we developed and refined algorithms capable of operating across both structured games and dynamic forecasting tasks. While our models have shown strong results in the game environment, development in the weather and energy domains remains ongoing, with promising progress expected in the coming semesters.

## Objective

The primary objective was to dramatically improve the Goat player’s performance using value iteration and other RL techniques, achieving a higher win rate than baseline strategies like random or greedy play.

Beyond winning the game, the project aimed to understand how these models could generalize to complex, data-driven systems, specifically weather and power forecasting. This required adapting discrete decision-making strategies from the game to continuous, unpredictable environments with noisy inputs. Scalability, generalization, and adaptability became criteria for this transition.

Additionally, the project served as a hands-on application of prior coursework in machine learning, algorithms, and AI. Tools like the OpenSpiel API allowed us to quickly prototype and evaluate various strategies, forming a bridge between theoretical foundations and practical innovation. Ultimately, the objective was not just to succeed in a game setting, but to build a versatile framework capable of impacting real-world systems such as energy distribution and climate prediction.

## Methodology

1. **Data Collection and Preprocessing:**

   - Gather a diverse dataset of Tigers and Goats gameplay scenarios, including various strategies employed by human players.
   - Preprocess the data to extract meaningful features, ensuring the model captures the nuanced aspects of the game.

2. **Machine Learning Models:**

   - Implement neural network architectures to facilitate learning and decision-making processes.
   - Utilize Large Language Models to enhance the system's understanding of natural language instructions and interactions related to the game.

3. **Training Process:**

   - Employ reinforcement learning techniques to train the system by exposing it to the collected dataset.
   - Iteratively refine the model through feedback mechanisms, emphasizing adaptive learning.

4. **Python and TensorFlow Integration:**

   - Develop the system using Python as the core programming language, capitalizing on its versatility and extensive machine-learning libraries.
   - Leverage TensorFlow for building, training, and deploying neural networks, ensuring efficiency and scalability.

5. **Evaluation and Fine-Tuning:**
   - Assess the performance of the trained models through simulations and gameplay scenarios.
   - Fine-tune the algorithms based on the observed outcomes, aiming for continual improvement.

## Significance

The successful implementation of an autonomous gameplay agent for Tigers and Goats holds significance in multiple domains:

- **Artificial Intelligence in Gaming:** Showcase the prowess of machine learning in mastering complex strategy games.
- **Reinforcement Learning:** Contribute to developing reinforcement learning algorithms by applying them to a real-world gaming scenario.
- **Practical AI Applications:** Explore the potential of autonomous agents for strategic decision-making in various contexts beyond gaming.

## Conclusion

This project seeks to push the boundaries of artificial intelligence by applying cutting-edge machine-learning techniques to the traditional board game Tigers and Goats. The amalgamation of Python, TensorFlow, and significant language models ensures a comprehensive and innovative approach to creating intelligent gameplay agents. The successful execution of this project promises not only advancements in gaming AI but also valuable insights into the broader applications of machine learning in strategic decision-making scenarios.

Used ChatGPT for Formating and Proof reading.
