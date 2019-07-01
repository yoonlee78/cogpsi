### Reinforcement Learning : Introduction

#### 2019.7.1.Tue

#### CogPsi Study

#### YK LEE

----

#### 자료 
1. Reinforcement Learning: Introduction 
2. Reinforcement Learning Lecture Notes by David. Silver
3. 케라스와 파이썬으로 배우는 강화학습. 이웅원 외. 위키북스. 

----
#### 차례

I. What is Reinforcement Learning? <br>
II. Components: Agent, State, and Reward<br>
III. Features
IV. How learning works: MDP <br> 
V. Examples of RL: DeepMind 'Breakout' <br>

---

## I. What is Reinforcement Learning?

### 1. Definition.

- a **computational** approach to learning from interaction.
- perspective of an AI researcher or engineer
- much more focused on goal-directed from interaction than other apporaches to machine learning
- learning what to do (map situations to actions, _'policy'_) to maximize a numerical reward signal

- Characteristics:
    - trial-and-error search
    - delayed reward

- Formalization
    - dynamical systems theory
    - Markov decision process

### 2. Machine Learning 
 (pic1)
 Supervised, unsupervised, and Reinforcement Learning

   - supervised learning? <br>
      - supervisor Y/N
      - labeled examples Y/N

    - unsupervised learning? <br>
      - reward-seeking? Y/N <br>
      - hidden structure = reward maximizing action ? Y/N <br>

----

II. Components: Agent, State, and Reward

(pic2)

#### 1. Agent

1.1. Def. 
the learner who can sense the 'state' of its 'environment' to some extent and take 'actions' that affect the state.

- in Psychology, any living/unliving 'being'
- in RL, a computer. 

1.2. In RL, an agent has a *goal*.  <br>
    the agents must have _a goal or goals_ relating to the state of the environment (_continued in 5. Goal of the agent_)

1.3. the agent takes 'action' <br>

#### 2. State 

2.1. Def. 
the representation of the environment. 
Often, state = environment. 
state can be noted as S_t 

2.2. Example: Go game (pic3)

#### 3. Reward

3.1. Def. 
the signal(feedback) that an environment(state) send out to the agent. It can be single value and stochastic functions of the state and actions taken. **An agent must maximize the total reward over the long run.** 

3.2. Role of the reward: 
it gives the agent an opportunity to evaluate whether the event is **good** or **bad**

3.3. Types of Reward

Reward can be negative (= 'punishment' in Psychology)

value = total amount of reward an agent can expect in the **long run**. (reward = immediate event, value = 'long-term')

3.4. "적절한" 보상

In Psychological perspecitve: 
    - 보상의 양 
    - 보상의 타이밍 (e.g., blocking, Hierarchy of Conditiong, Rescolar-Wagner, 1972)
    - 보상의 종류 (+, -)
    - 보상을 주는 방법 : Stimulus-Response (UR, CR, US, CS) and classical conditioning (Ian Pavlov, 1927) operant conditioning (role of 'reinforcer', Thorndike, 1898; Skinner, 1938, 1961)

Based on the reward, an agent may **change the policy**

#### 4. Policy

association/mapping between action and state

"모든 상태에 대해 에이젼트가 어떤 행동을 해야하는 지 정해놓은 것"

심리학의 자극-반응 연합과 같은 이치.

The optimal policy = the one guarentees max(reward)

#### 5. Goal of the agent
(pic3)

5.1. Goal 1
    상태가 주어졌을 때 어떤 행동을 해야하는 지를 배워야한다 (learn the policy)

5.2. Goal 2
    어떤 상태에서는 어떤 행동을 해야 최대의 보상(max(reward)을 받을 수 있는지를 배워야한다 = learn 'optimal policy'.

III. Features <br>

- planning (revisit later) <br>
- no prior knowledge is necessary
- explore vs exploit (revisit)

explore vs exploit example ([OpenAI Gym](https://gym.openai.com/)) <br>

<video controls="" autoplay="" name="media"><source src="https://gym.openai.com/videos/2019-05-31--eRh4Fbp8G5/CartPole-v1/original.mp4" type="video/mp4"></video>

video [link]("https://gym.openai.com/videos/2019-05-31--eRh4Fbp8G5/CartPole-v1/original.mp4"/)

<img src = "./img/pole_result.png"/>


### IV. How learning works: MDP <br> 

"강화학습은 "결정을 순차적으로 내려야 하는 문제"에 적용됨"

<문제 정의>
결정을 순차적으로 내려야하는 문제를 '수학적'으로 표현할 수 있어야함. 

1. MDP

"**Markov decision process** is the simplest possible form (formalization) of sensation, action, and goal."(Sutton).

2. Components of 'MDP'

- state 
- action
- reward

3. Example: 

- **Chess player**: planning and intuitive judgemnts of the desirability of particular positions and moves

- **a mobile robot**: entering a new room to search more trash. decision: should I move forward or go back to charging station? monitoring current charge level of its batterly + how quickly and easily it has been able to find the recharger in the past

- Soccer Player ?

- Super Mario ?

----

"Playing Atari with Deep Reinforcement Learning by DeepMind"

[Breakout](https://www.youtube.com/watch?v=TmPfTpjtdgg)

1. MDP Definition (according to DeepMind)

1.1. State

= Game Screen (4 sequential 2D image pixel data as a state)

<img src = "https://neuro.cs.ut.ee/wp-content/uploads/2015/12/breakout_deepmind.png">

1.2. Action

Left, Right, Hold, Fire

한 state에서 최소 4번의 action 반복 (하나의 상태 = 화면 4개)

1.3. Reward

벽돌 하나 깨면 +1
더 위를 깨면 +a
아무 것도 깨지 않으면 0
죽으면 -1

2. Learning (**to revisit later in Chapter 05**)

(1) 처음에는 아무 것도 모름 => (2) 몇 개 깨기 시작 -> (3) 보상

(2)와 (3)의 반복. 

Neural Network of Learning
- input = state
- output = Q function

Q function : 행동이 얼마나 좋은지에 대한 확률 값. 상태 i에서 Q 함수가 나온 다음 보상이 부여되고 다음 상태 (state_i+1)rk dlqfurehlsek. Agent는 이 Q 함수에 따라 움직인다 (즉, action을 택한다). DeepMind는 DQN (Deep Q-Network)에서 이 Q function을 CNN을 사용하였고, max(DQN)하는 action_j를 찾는 것이 RL agent의 목적.

그 외 DQN이 특별한 점 (replay buffer, target neural network + learning network..etc.)은 이후 챕터에서 revisit. 





