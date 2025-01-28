Ребята из **DeepSeek** хотели посмотреть, нам SFT вот прям всегда нужен?

В качестве базы взяли свою [DeepSeek V3](https://github.com/deepseek-ai/DeepSeek-V3) (671 миллиард параметров) модельку.  

RL-алгоритм взяли тоже свой - **Group Relative Policy Optimization (GRPO)** который впервые представили в статье  

**DeepSeekMath: Pushing the Limits of Mathematical Reasoning in Open Language Models**  
https://arxiv.org/abs/2402.03300

![image](https://github.com/user-attachments/assets/f98d631a-f800-4828-8d44-35a7d8063e96)

**GRPO:**

Генерируем нескольких ответов на один и тот же вопрос, получаем группу ответов  
Награда нормализуется внутри этой группы ответов. (Group в названии метода становится понятнее)  
Модель учится уже на этих нормализованных наградах.  

Вообще PPO алгоритм (сам по себе, не только в контексте обучения LLM) требует обучения двух моделей - **policy** и **value** (actor/critic). policy у нас так сказать главная нейронка, value - вспомогательная и нужна именно для обучения. В GRPO нужен только **policy**.

Так-то всё здесь:
https://github.com/deepseek-ai/DeepSeek-R1
