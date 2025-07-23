---
title: "Asymmetry of Verification and Verifier’s Law | 验证的非对称性与验证者法则"
date: 2025-07-23T21:00:00+08:00
draft: false
---

> 原文：https://www.jasonwei.net/blog/asymmetry-of-verification  
> 作者：Jason Wei  
> 翻译：[Harry Wong](https://github.com/harryisfish)  
> 校对、排版：Cursor IDE  

Asymmetry of verification is the idea that some tasks are much easier to verify than to solve. With reinforcement learning ([RL](#glossary-reinforcement-learning)) that finally works in a general sense, [asymmetry of verification](#glossary-asymmetry-of-verification) is becoming one of the most important ideas in AI.

[验证的非对称性](#glossary-asymmetry-of-verification)指的是某些任务验证起来比解决本身要容易得多。随着[强化学习](#glossary-reinforcement-learning)（RL）在通用意义上取得突破，验证的非对称性正成为人工智能领域最重要的思想之一。

Understanding [asymmetry of verification](#glossary-asymmetry-of-verification) through examples

通过例子理解[验证的非对称性](#glossary-asymmetry-of-verification)

[Asymmetry of verification](#glossary-asymmetry-of-verification) is everywhere, if you look for it. Some prime examples:

如果你留心观察，[验证的非对称性](#glossary-asymmetry-of-verification)无处不在。以下是一些典型例子：

Sudoku and crossword puzzles take a lot of time to solve because you have to try many candidates against various constraints, but it is trivial to check if any given solution is correct.

数独和填字游戏需要花费大量时间来解答，因为你需要在各种约束下尝试许多候选答案，但检查一个给定解是否正确却非常简单。

Writing the code to operate a website like instagram takes a team of engineers many years, but verifying whether the website is working properly can be done quickly by any layperson.

开发一个像 Instagram 这样的网站需要一支工程师团队多年努力，但任何普通人都可以很快验证网站是否正常运行。

Solving BrowseComp problems often requires browsing hundreds of websites, but verifying any given answer can often be done much more quickly because you can directly search if the answer meets the constraints.

解决 BrowseComp 问题通常需要浏览数百个网站，但验证某个答案是否符合约束条件往往要快得多，因为你可以直接检索答案是否满足要求。

Some tasks have near-symmetry of verification: they take a similar amount of time to verify as to write a solution. For example, verifying the answer to some math problems (e.g., adding two 900-digit numbers) often takes the same amount of work as solving the problem yourself. Another example is some data processing programs; following someone else’s code and verifying that it works takes just as long as writing the solution yourself.

有些任务的验证几乎是对称的：验证和解决所需的时间差不多。例如，验证某些数学题的答案（比如两个900位数相加）通常和自己解题一样费力。再比如某些数据处理程序，跟着别人的代码验证其正确性和自己写一遍所需的时间差不多。

Interestingly, there are also some tasks that can take way longer to verify than to propose a solution. For example, it might take longer to fact-check all the statements in an essay than to write that essay (cue [Brandolini's law](#glossary-brandolinis-law): “The amount of energy needed to refute bullshit is an order of magnitude bigger than that needed to produce it.”). Many scientific hypotheses are also harder to verify than to come up with. For example, it is easy to state a novel diet (“Eat only bison and broccoli”) but it would take years to verify whether the diet is beneficial for a general population.

有趣的是，也有一些任务验证起来比提出解决方案要难得多。例如，核查一篇文章中的所有陈述可能比写这篇文章还要花时间（参见[布兰多里尼定律](#glossary-brandolinis-law)：“驳斥胡说八道所需的能量比制造胡说八道多一个数量级。”）。许多科学假说的验证也比提出要难得多。例如，提出一种新饮食法（“只吃野牛和西兰花”）很容易，但要验证这种饮食对大众是否有益却需要数年时间。

Improving [asymmetry of verification](#glossary-asymmetry-of-verification)

提升[验证的非对称性](#glossary-asymmetry-of-verification)

One of the most important realizations about [asymmetry of verification](#glossary-asymmetry-of-verification) is that it is possible to actually improve the asymmetry by front-loading some research about the task. For example, for a competition math problem, it is trivial to check any proposed final answer if you have the answer key at hand. Another great example is some coding problems: while it’s tedious to read code and check its correctness, if you have test cases with ample coverage, you can quickly check any given solution; indeed, this is what Leetcode does. In some tasks, it is possible to improve verification but not enough to make it trivial. As an example, for a problem like “Name a Dutch soccer player”, it would help to have a list of the famous Dutch soccer players but verification would still require work in many cases.

关于[验证非对称性](#glossary-asymmetry-of-verification)的一个重要认识是：通过前置一些研究，可以实际提升验证的非对称性。例如，做竞赛数学题时，如果手头有答案，检查任何一个最终答案就变得非常简单。另一个例子是编程题：虽然阅读代码并检查其正确性很繁琐，但如果有覆盖充分的测试用例，就可以快速验证任何解法，这正是 Leetcode 的做法。在某些任务中，虽然可以提升验证效率，但还不足以让验证变得完全简单。例如，“说出一位荷兰足球运动员”这种题目，如果有著名荷兰球员名单会有帮助，但很多情况下验证仍需花费精力。

[Verifier’s law](#glossary-verifiers-law)

[验证者法则](#glossary-verifiers-law)

Why is [asymmetry of verification](#glossary-asymmetry-of-verification) important? If you consider the history of deep learning, we have seen that virtually anything that can be measured can be optimized. In [RL](#glossary-reinforcement-learning) terms, ability to verify solutions is equivalent to ability to create an [RL environment](#glossary-rl-environment). Hence, we have:

为什么[验证的非对称性](#glossary-asymmetry-of-verification)很重要？回顾深度学习的发展史，我们会发现几乎所有可度量的东西都能被优化。用[强化学习](#glossary-reinforcement-learning)的术语来说，能验证解法就等于能构建[RL 环境](#glossary-rl-environment)。因此，我们有：

[Verifier’s law](#glossary-verifiers-law): The ease of training AI to solve a task is proportional to how verifiable the task is. All tasks that are possible to solve and easy to verify will be solved by AI.

[验证者法则](#glossary-verifiers-law)：训练 AI 解决某项任务的难易程度与该任务的可验证性成正比。所有可解且易于验证的任务都将被 AI 解决。

More specifically, the ability to train AI to solve a task is proportional to whether the task has the following properties:

更具体地说，训练 AI 解决任务的能力与任务是否具备以下特性成正比：

[Objective truth](#glossary-objective-truth): everyone agrees what good solutions are

[客观真理](#glossary-objective-truth)：所有人都认同什么是好解法

Fast to verify: any given solution can be verified in a few seconds

验证迅速：任何给定解法都能在几秒内验证

[Scalable to verify](#glossary-scalable-verification): many solutions can be verified simultaneously

[可扩展验证](#glossary-scalable-verification)：可以同时验证大量解法

[Low noise](#glossary-low-noise): verification is as tightly correlated to the solution quality as possible

[低噪声](#glossary-low-noise)：验证结果与解法质量高度相关

[Continuous reward](#glossary-continuous-reward): it’s easy to rank the goodness of many solutions for a single problem

[连续奖励](#glossary-continuous-reward)：可以轻松对同一问题的多个解法进行优劣排序

It’s not hard to believe that [verifier’s law](#glossary-verifiers-law) holds true: most [benchmarks](#glossary-benchmark) that have been proposed in AI are easy to verify and so far have been solved. Notice that virtually all popular benchmarks in the past ten years fit criteria #1-4; benchmarks that don’t meet criteria #1-4 would struggle to become popular. Note that although most benchmarks don’t fit criteria #5 (a solution is either strictly correct or not), you can compute a [continuous reward](#glossary-continuous-reward) by averaging the binary reward of many examples.

[验证者法则](#glossary-verifiers-law)的正确性并不难理解：AI 领域提出的大多数[基准测试](#glossary-benchmark)都易于验证，并且至今都已被攻克。注意，过去十年几乎所有流行的基准测试都符合前四条标准；不符合这些标准的基准测试很难流行起来。虽然大多数基准测试不符合第5条（解法要么完全正确要么完全错误），但你可以通过对大量样本的二元奖励取平均来计算[连续奖励](#glossary-continuous-reward)。

Why is verifiability so important? In my view, the most basic reason is that the amount of learning that occurs in neural networks is maximized when the above criteria are satisfied; you can take a lot of [gradient](#glossary-gradient) steps where each step has a lot of signal. Speed of iteration is critical—it’s the reason that progress in the digital world has been so much faster than progress in the physical world.

为什么可验证性如此重要？在我看来，最根本的原因是：当上述标准被满足时，神经网络的学习量最大化——每一步[梯度](#glossary-gradient)更新都包含大量有效信号。迭代速度至关重要，这也是数字世界进步远快于物理世界的原因。

AlphaEvolve

AlphaEvolve

Perhaps the greatest public example of leveraging [asymmetry of verification](#glossary-asymmetry-of-verification) in the past few years is AlphaEvolve, developed by Google. In short, AlphaEvolve can be seen as a very clever instantiation of guess-and-check that allows for ruthless optimization of an objective, which has resulted in several mathematical and operational innovations.

过去几年中，最能体现[验证非对称性](#glossary-asymmetry-of-verification)优势的公开案例或许就是 Google 开发的 AlphaEvolve。简而言之，AlphaEvolve 可以看作是一种极为巧妙的“猜测-验证”机制实例，能够对目标进行极致优化，并带来了多项数学和操作上的创新。

A simple example of a problem optimized by AlphaEvolve is something like “Find the smallest outer hexagon that fits 11 unit hexagons.” Notice that this problem fits all five desirable properties of [verifier’s law](#glossary-verifiers-law). Indeed, my belief is that any solvable problem that fits those five properties will be solved in the next few years.

AlphaEvolve 优化过的一个简单问题是“找到能容纳11个单位正六边形的最小外部正六边形”。注意，这个问题完全符合[验证者法则](#glossary-verifiers-law)的五个理想特性。实际上，我相信未来几年内，所有符合这五个特性的可解问题都将被攻克。

One thing about the types of problems solved by AlphaEvolve is that it can be seen as “[overfitting](#glossary-overfitting)” to a single problem. In traditional machine learning, we already know the labels in the training set and the significant test was to measure generalization to unseen problems. However, in scientific innovation, we are in a totally different realm where we only care about solving a single problem (train=test!) because it’s an unsolved problem and potentially extremely valuable.

AlphaEvolve 所解决的问题有一个特点，就是它可以被视为对单一问题的“[过拟合](#glossary-overfitting)”。在传统机器学习中，我们已知训练集标签，关键考验在于对未知问题的泛化能力。但在科学创新领域，我们处于完全不同的情境——我们只关心解决某个具体问题（训练集=测试集！），因为这是一个尚未解决且极具价值的问题。

Implications

启示

Once you’ve learned about it, you’ll notice that [asymmetry of verification](#glossary-asymmetry-of-verification) is everywhere. It’s exciting to consider a world where anything we can measure will be solved. We will likely have a jagged edge of intelligence, where AI is much smarter at verifiable tasks because it’s so much easier to solve verifiable tasks. What an exciting future to consider.

一旦你了解了[验证的非对称性](#glossary-asymmetry-of-verification)，你会发现它无处不在。想象一个任何可度量问题都能被解决的世界令人振奋。我们很可能会迎来“锯齿状”的智能边界——AI 在可验证任务上远超人类，因为这些任务更容易被攻克。多么令人期待的未来！

---

## 名词解析

- <span id="glossary-asymmetry-of-verification"></span>**Asymmetry of verification**：The idea that some tasks are much easier to verify than to solve. 某些任务验证起来比解决本身要容易得多的思想。
- <span id="glossary-verifiers-law"></span>**Verifier’s law**：The ease of training AI to solve a task is proportional to how verifiable the task is. 训练 AI 解决任务的难易程度与任务的可验证性成正比。
- <span id="glossary-reinforcement-learning"></span>**Reinforcement learning (RL)**：A type of machine learning where agents learn to make decisions by receiving rewards or penalties. 一种通过奖励或惩罚让智能体学习决策的机器学习方法。
- <span id="glossary-brandolinis-law"></span>**Brandolini's law**：The amount of energy needed to refute bullshit is an order of magnitude bigger than that needed to produce it. 驳斥胡说八道所需的能量比制造胡说八道多一个数量级。
- <span id="glossary-objective-truth"></span>**Objective truth**：A state where everyone agrees on what constitutes a correct or good solution. 所有人都认同的客观正确答案或标准。
- <span id="glossary-scalable-verification"></span>**Scalable verification**：The ability to verify many solutions simultaneously, often through automation or parallel processes. 能够同时验证大量解法的能力，通常依赖自动化或并行处理。
- <span id="glossary-low-noise"></span>**Low noise**：Verification results are highly correlated with the true quality of the solution, with minimal random error. 验证结果与解法质量高度相关，随机误差极小。
- <span id="glossary-continuous-reward"></span>**Continuous reward**：A reward system where solution quality can be ranked or scored on a spectrum, not just right or wrong. 奖励机制可以对解法优劣进行连续打分，而非仅有对错。
- <span id="glossary-overfitting"></span>**Overfitting**：A model or method that performs well on a specific problem or dataset but fails to generalize to new problems. 只对特定问题或数据集表现良好，但无法泛化到新问题的现象。
- <span id="glossary-benchmark"></span>**Benchmark**：A standard test or set of problems used to evaluate the performance of AI systems. 用于评估 AI 系统性能的标准测试或问题集。
- <span id="glossary-gradient"></span>**Gradient**：In machine learning, the direction and rate of change used to update model parameters during training. 机器学习中用于更新模型参数的变化方向和速率。
- <span id="glossary-rl-environment"></span>**RL environment**：A simulated or real-world setting in which a reinforcement learning agent interacts and learns from feedback. 强化学习智能体与之交互并通过反馈学习的模拟或真实环境。 