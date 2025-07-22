---
title: "Life lessons from reinforcement learning | 强化学习带给我的人生启示"
date: 2025-07-23T01:39:00+08:00
draft: false
---

> 原文：https://www.jasonwei.net/blog/life-lessons-from-reinforcement-learning  
> 作者：Jason Wei  
> 翻译：[Harry](https://github.com/harryisfish)  
> 校对、排版：Cursor IDE  

Becoming an [RL](#glossary-rl) diehard in the past year and thinking about RL for most of my waking hours inadvertently taught me an important lesson about how to live my own life.

成为[强化学习（RL）](#glossary-rl)铁粉的一年里，我几乎每天都在思考RL，这无意中教会了我一条重要的人生经验。

One of the big concepts in RL is that you always want to be “[on-policy](#glossary-on-policy)”: instead of mimicking other people’s successful trajectories, you should take your own actions and learn from the reward given by the [environment](#glossary-environment). Obviously [imitation learning](#glossary-imitation-learning) is useful to [bootstrap](#glossary-bootstrap) to nonzero [pass rate](#glossary-pass-rate) initially, but once you can take reasonable [trajectories](#glossary-trajectory), we generally avoid imitation learning because the best way to leverage the [model](#glossary-model)’s own strengths (which are different from humans) is to only learn from its own trajectories. A well-accepted instantiation of this is that RL is a better way to train language models to solve math word problems compared to simple [supervised finetuning](#glossary-supervised-finetuning) on human-written [chains of thought](#glossary-chain-of-thought).

强化学习中的一个重要概念是始终保持“[在线策略](#glossary-on-policy)”：与其模仿他人的成功[轨迹](#glossary-trajectory)，不如采取自己的行动并从[环境](#glossary-environment)给予的奖励中学习。显然[模仿学习](#glossary-imitation-learning)在初期能有效实现非零[通过率](#glossary-pass-rate)，但一旦能生成合理轨迹，我们通常会避免模仿学习，因为发挥[模型](#glossary-model)自身优势（与人类不同）的最佳方式就是仅从其自身轨迹中学习。一个公认的实例是：相较于对人类书写[思维链](#glossary-chain-of-thought)进行简单[监督微调](#glossary-supervised-finetuning)，强化学习才是训练语言模型解决数学应用题更有效的方法。

Similarly in life, we first bootstrap ourselves via imitation learning (school), which is very reasonable. But even after I graduated school, I had a habit of studying how other people found success and trying to imitate them. Sometimes it worked, but eventually I realized that I would never surpass the full ability of someone else because they were playing to their strengths which I didn’t have. It could be anything from a researcher doing [yolo runs](#glossary-yolo) more successfully than me because they built the codebase themselves and I didn’t, or a non-AI example would be a soccer player keeping ball possession by leveraging strength that I didn’t have.

同样地，在生活中，我们最初通过模仿学习（比如上学）来为自己打基础，这是很合理的。但即使毕业后，我也习惯于研究他人如何获得成功并试图模仿。有时确实有效，但最终我意识到，永远无法超越他人的全部能力，因为他们在发挥自己独有的优势，而我并不具备。比如有的研究者能更好地做[yolo实验](#glossary-yolo)，是因为他们自己搭建了代码库，而我没有；又比如足球运动员能更好地控球，是因为他们有我没有的身体素质。

The lesson of doing RL on policy is that beating the teacher requires walking your own path and taking risks and rewards from the environment. For example, two things I enjoy more than the average researcher are (1) reading a lot of [data](#glossary-dataset), and (2) doing [ablations](#glossary-ablation) to understand the effect of individual [components](#glossary-component) in a system. Once when collecting a dataset, I spent a few days reading data and giving each human [annotator](#glossary-annotator) personalized feedback, and after that the data turned out great and I gained valuable insight into the task I was trying to solve. Earlier this year I spent a month going back and ablating each of the decisions that I previously yolo’ed while working on deep research. It was a sizable amount of time spent, but through those experiments I learned unique lessons about what type of RL works well. Not only was leaning into my own passions more fulfilling, but I now feel like I’m on a path to carving a stronger [niche](#glossary-niche) for myself and my research.

RL中“在线策略”的启示是：想要超越老师，必须走自己的路，从环境中获得属于自己的风险和回报。例如，我比一般研究者更喜欢两件事：（1）阅读大量[数据](#glossary-dataset)；（2）做[消融实验](#glossary-ablation)以理解系统中各个[组件](#glossary-component)的作用。有一次收集数据集时，我花了几天时间阅读数据并给每位人工[标注员](#glossary-annotator)个性化反馈，结果数据质量非常好，我也对要解决的任务有了宝贵的洞见。今年早些时候，我花了一个月时间回头对自己在深度研究中“yolo”做出的每个决策都做了消融。虽然花了不少时间，但这些实验让我学到了哪些RL方法真正有效的独特经验。不仅更有成就感，也让我觉得自己正在为自己和研究开辟更强的[专属领域](#glossary-niche)。

In short, imitation is good and you have to do it initially. But once you’re bootstrapped enough, if you want to beat the teacher you must do on-policy RL and play to your own strengths and weaknesses :)

简而言之，模仿是好的，起步时必须要做。但一旦你有了基础，如果想超越老师，就必须做“在线策略”RL，发挥自己的优势和劣势：）

---

## 名词解析

- <span id="glossary-rl"></span>**RL**：Reinforcement Learning（强化学习），一种让计算机通过“试错”获得经验并改进自己的方法。
- <span id="glossary-on-policy"></span>**on-policy**：在线策略，指的是自己做决定、自己学习，而不是只模仿别人。
- <span id="glossary-imitation-learning"></span>**imitation learning**：模仿学习，通过模仿别人的做法来学习。
- <span id="glossary-bootstrap"></span>**bootstrap**：在这里指“起步”或“打基础”，就是刚开始学习时用的方法。
- <span id="glossary-pass-rate"></span>**pass rate**：通过率，指做对的次数占总次数的比例。
- <span id="glossary-trajectory"></span>**trajectory/trajectories**：轨迹，指做事的过程或一连串的动作。
- <span id="glossary-environment"></span>**environment**：环境，在强化学习里指的是和你互动、给你反馈的世界。
- <span id="glossary-model"></span>**model**：模型，这里指的是计算机用来学习和做决定的“聪明大脑”。
- <span id="glossary-supervised-finetuning"></span>**supervised finetuning**：有监督微调，用人类写的答案来教计算机。
- <span id="glossary-chain-of-thought"></span>**chain of thought**：思维链，把思考的每一步都写出来。
- <span id="glossary-ablation"></span>**ablation/doing ablations**：消融实验，把一个系统的部分拿掉，看看会发生什么，从而了解每一部分的作用。
- <span id="glossary-dataset"></span>**dataset**：数据集，一堆用来学习或测试的数据。
- <span id="glossary-annotator"></span>**annotator**：标注员，帮忙给数据加标签或说明的人。
- <span id="glossary-yolo"></span>**yolo runs**：yolo 是“you only live once”的缩写，这里指大胆尝试、不怕失败地做实验。
- <span id="glossary-component"></span>**component**：组件，系统里的一个小部分。
- <span id="glossary-niche"></span>**niche**：专属领域，指自己特别擅长、别人不太会的地方。 