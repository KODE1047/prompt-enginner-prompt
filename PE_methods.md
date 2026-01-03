#### **1. Zero-shot Prompting**

* **Analysis:** The baseline. Relying purely on the model's pre-training distribution without providing examples.
* **Use Case:** Simple, high-probability tasks (e.g., sentiment analysis).
* **Example:**
```text
Classify the text into neutral, negative, or positive.
Text: I think the vacation is okay.
Sentiment:

```



#### **2. Few-shot Prompting (In-Context Learning)**

* **Analysis:** Providing  examples (where  typically) to steer the model. This drastically reduces the search space for the model.
* **Use Case:** Complex formatting or specific output styles.
* **Example:**
```text
Great product -> Positive
Bad service -> Negative
Okay food -> Neutral
I think the vacation is okay ->

```



#### **3. Chain-of-Thought (CoT)**

* **Analysis:** The single most important technique. It forces the model to generate a "rationale" *before* the answer. This decouples reasoning from answering.
* **Use Case:** Math, Logic, Strategic Planning.
* **Example:**
```text
Q: Roger has 5 tennis balls. He buys 2 more cans of tennis balls. Each can has 3 tennis balls. How many tennis balls does he have now?
A: Let's think step by step.
1. Roger starts with 5 balls.
2. He buys 2 cans.
3. Each can has 3 balls, so 2 * 3 = 6 new balls.
4. Total = 5 + 6 = 11.
Answer: 11.

```



#### **4. Meta-Prompting**

* **Analysis:** Using the LLM to write its own prompt. We optimize the *instructions* rather than the task itself.
* **Use Case:** When you don't know how to articulate the task clearly.
* **Example:**
```text
I want to solve a complex scheduling problem.
Write a prompt that I can give to an AI to solve this problem effectively. Include constraints and role definition.

```



#### **5. Self-Consistency**

* **Analysis:** Instead of taking the first answer (Greedy Decoding), we sample  answers (e.g., 5 CoT paths) and take the majority vote. This filters out stochastic hallucinations.
* **Use Case:** High-stakes reasoning where accuracy is paramount.
* **Example:**
* *Run CoT 3 times.*
* Path A Result: 11
* Path B Result: 11
* Path C Result: 12
* *Final Decision:* 11 (Majority Vote).



#### **6. Generated Knowledge Prompting**

* **Analysis:** Forcing the model to "dump" relevant facts before answering a question. This primes the context window with accurate data from its own weights.
* **Use Case:** Answering questions about obscure topics where the model might hallucinate if rushed.
* **Example:**
```text
Q: Is a golf ball larger than a pebble?
Generate Knowledge: A standard golf ball is about 42.67mm. A pebble usually ranges from 4mm to 64mm.
Answer: It depends, but a golf ball is within the size range of a large pebble.

```



#### **7. Prompt Chaining**

* **Analysis:** Breaking a complex task into sequential sub-tasks. The output of Prompt A becomes the input of Prompt B.
* **Use Case:** Long document summarization or multi-step logic (Extract -> Analyze -> Format).
* **Example:**
* *Step 1:* "Extract all dates from this email." -> `[Jan 12, Feb 10]`
* *Step 2:* "Check if these dates are available in my calendar: `[Jan 12, Feb 10]`"



#### **8. Tree of Thoughts (ToT)**

* **Analysis:** Generalizing CoT into a search tree (BFS/DFS). The model generates multiple "next steps," evaluates them, and backtracks if necessary.
* **Use Case:** Creative writing, coding, strategic planning.
* **Example:**
* *Goal:* Write a poem.
* *Thought 1:* Rhyme scheme AABB. (Eval: Too simple).
* *Thought 2:* Free verse about nature. (Eval: Good). -> *Continue this path.*



#### **9. Retrieval Augmented Generation (RAG)**

* **Analysis:** Injecting non-parametric knowledge (external docs) into the prompt context. This fixes the "knowledge cutoff" and hallucination issues.
* **Use Case:** Answering questions about private company data or recent news.
* **Example:**
```text
Context: [Snippet from 2025 User Manual: "Press the Red Button to restart."]
Q: How do I restart?
A: Based on the manual, press the Red Button.

```



#### **10. Automatic Reasoning and Tool-use (ART)**

* **Analysis:** A framework where the model pauses generation to call external tools (like search or code execution) when it detects a specific token pattern.
* **Use Case:** Mixed-mode tasks (e.g., "Research this topic and then plot a graph").

#### **11. Automatic Prompt Engineer (APE)**

* **Analysis:** Treating the "instruction" as a variable to be optimized. An LLM generates candidate prompts, tests them, and selects the best one (Gradient-free optimization).
* **Use Case:** Finding the "magic words" (like "Let's work this out...") that maximize performance.

#### **12. Active-Prompt**

* **Analysis:** Uncertainty-based learning. The model identifies which questions it is "unsure" about (high entropy/disagreement) and asks a human to annotate *those specific examples* for Few-Shot prompting.
* **Use Case:** Optimizing a Few-Shot prompt with limited human labeling budget.

#### **13. Directional Stimulus Prompting (DSP)**

* **Analysis:** Using a small, tunable model to generate "hints" or "keywords" that guide the main large model. It acts as a compass for the black box.
* **Use Case:** Summarization where you want to focus on specific aspects (e.g., "Focus on the financial numbers").

#### **14. Program-Aided Language Models (PAL)**

* **Analysis:** Offloading computation to a Python interpreter. Instead of "thinking" the math, the model writes code to calculate it.
* **Use Case:** Arithmetic, heavy calculation.
* **Example:**
```text
Q: What is the square root of 12345?
Model Output:
import math
print(math.sqrt(12345))

```



#### **15. ReAct (Reasoning + Acting)**

* **Analysis:** An interleaved loop: `Thought` -> `Action` -> `Observation`. The model reasons about what to do, does it (via tool), observes the result, and reasons again.
* **Use Case:** Autonomous agents.
* **Example:**
```text
Thought: I need to find the weather in Tokyo.
Action: weather_api("Tokyo")
Observation: 15°C, Rain.
Thought: It is raining, so I should suggest an umbrella.
Final Answer: Bring an umbrella.

```



#### **16. Reflexion**

* **Analysis:** ReAct with a "verbal reinforcement" loop. If the agent fails, it writes a self-critique ("I failed because X") and stores it in memory for the next attempt.
* **Use Case:** Complex coding tasks or games where trial-and-error is needed.
* **Example:**
* *Attempt 1:* Fails to compile code.
* *Reflexion:* "I forgot to import the library."
* *Attempt 2:* Writes code *with* the import.



#### **17. Multimodal CoT**

* **Analysis:** Applying Chain-of-Thought reasoning where the inputs (or intermediate steps) involve both text and images.
* **Use Case:** Answering questions about charts, diagrams, or physical world scenarios.
* **Example:**
* *Input:* Image of a geometry problem.
* *Thought:* "The image shows a triangle with base 5 and height 4."
* *Calculation:* "Area = 0.5 * 5 * 4 = 10."