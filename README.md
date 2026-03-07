# ⚡ Prompt Engineering Playbook
*A structured, practical guide to writing better AI prompts — designed to teach, demonstrate, and inspire. Built as a showcase of real prompt engineering expertise.*

> [!NOTE] 
> **Portfolio Project**  
> 📖 5 Core Techniques | ⚠️ 6 Common Mistakes | 🎓 3 Lesson Plans | 🏆 1 Capstone Challenge

---

## ① What is Prompt Engineering?
Prompt engineering is the practice of designing and refining inputs to AI language models to reliably produce desired outputs. It sits at the intersection of communication, critical thinking, and AI literacy.

> [!TIP] 💡 Core Insight
> AI models don't read minds — they respond to what you actually write. The quality of your output is directly proportional to the clarity, structure, and intent of your prompt.

A good prompt engineer doesn't just "talk to AI" — they **design interactions**. They think about: what role should the model play? What context does it need? What format should the output take? What should it avoid?

> [!NOTE] 🎯 Why This Matters for Tutors
> Teaching prompt engineering means helping others develop a new kind of literacy — one that will define how humans work with AI for decades. This playbook is both a skill showcase and a teaching resource.

---

## ② Core Concepts
*The mental models every prompt engineer must internalize.*

- 🎭 **Context Window**: The "working memory" of an AI model. Everything the model can "see" at once — your prompt, conversation history, and its response all live here.
- 🌡️ **Temperature**: Controls randomness. Low temperature (0.1) = predictable and factual. High temperature (0.9) = creative and varied. Match it to your use case.
- 🔁 **Iteration**: Prompting is rarely one-shot. The best results come from testing, observing outputs, and refining your prompt systematically — like debugging code.
- 🧩 **Grounding**: Giving the model concrete context, examples, or constraints to "anchor" its responses. The more specific the ground, the more reliable the output.
- ⚖️ **Instruction vs. Example**: You can tell a model what to do (instruction) or show it what you want (example). Examples often produce more consistent results than instructions alone.
- 🗺️ **Task Decomposition**: Breaking complex tasks into smaller sub-prompts. Instead of one giant prompt, guide the model step-by-step for far more reliable outputs.

---

## ③ Techniques Library
*Real prompts with before/after comparisons and explained reasoning.*

### 01. Zero-Shot Prompting 
*(Beginner)* - Asking the model to perform a task with no examples

**❌ Weak Prompt:**
```text
Write something about climate change.
```

**✅ Strong Prompt:**
```text
Write a 150-word explanation of climate change for a 12-year-old student. Use simple language, one real-world analogy, and end with one action they can take.
```

> [!TIP] 🔍 Why it works
> The strong prompt specifies the **audience** (12-year-old), **length** (150 words), **style** (simple + analogy), and **structure** (end with action). Every vague element is replaced with a concrete instruction. Zero-shot works best when instructions are specific enough to eliminate ambiguity.


### 02. Few-Shot Prompting
*(Beginner)* - Providing examples to show the model the expected pattern

**❌ Without Examples:**
```text
Classify these customer reviews as Positive, Neutral, or Negative:
"The delivery was late but the product is great."
```

**✅ With Examples (Few-Shot):**
```text
Classify each review. Examples:
"Love it!" → Positive
"It's okay, nothing special." → Neutral
"Broke after one use." → Negative

Now classify:
"The delivery was late but the product is great."
```

> [!TIP] 🔍 Why it works
> Examples anchor the model's interpretation of your categories. Without them, "Positive," "Neutral," and "Negative" are abstract — the model may weigh criteria differently than you intend. Three examples set a **pattern** that drastically improves consistency across varied inputs.

### 03. Chain-of-Thought (CoT)
*(Intermediate)* - Asking the model to reason step-by-step before answering

**❌ Direct Answer Request:**
```text
A store sells apples for $0.50 each and bags of 6 apples for $2.50. If I need 18 apples, what's the cheapest way to buy them?
```

**✅ Chain-of-Thought Prompt:**
```text
A store sells apples for $0.50 each and bags of 6 for $2.50. I need 18 apples.

Think through this step by step:
1. Calculate cost of buying 18 individual apples
2. Calculate cost of buying 3 bags of 6
3. Compare and recommend the cheaper option.
```

> [!TIP] 🔍 Why it works
> LLMs are statistically predicting the next token — they can "rush" to an answer without fully reasoning. CoT forces the model to **externalize its reasoning**, catching arithmetic or logic errors along the way. Research shows CoT can improve accuracy on multi-step reasoning tasks by 20–40%.

### 04. Role Prompting
*(Intermediate)* - Assigning the model an identity or expert persona

**❌ Generic Request:**
```text
Give me feedback on my business idea: a subscription box for local African snacks.
```

**✅ Role-Based Prompt:**
```text
You are a startup advisor who has helped 3 African e-commerce businesses scale from zero to $1M revenue.

Review this business idea critically: a subscription box for local African snacks targeting diaspora communities in the UK. 

Give 2 strengths, 2 risks, and 1 specific recommendation.
```

> [!TIP] 🔍 Why it works
> Role prompting activates a specific **frame of reference** in the model's training data — shifting tone, vocabulary, and the type of knowledge it draws on. A "startup advisor with African e-commerce experience" produces more contextually relevant feedback than a generic assistant.

### 05. Constraints & Output Formatting
*(Advanced)* - Controlling the shape, length, and structure of responses

**❌ No Format Control:**
```text
Summarise this article for me and tell me the key points.
```

**✅ Constrained Format Prompt:**
```text
Summarise the article below. Output format:

**One-Line Summary:** (max 20 words)
**Key Points:** (exactly 3 bullet points, each under 15 words)
**Audience:** (who would benefit from reading this?)

Do not include your opinion. Use plain language.

[ARTICLE TEXT HERE]
```

> [!TIP] 🔍 Why it works
> Explicit format instructions make outputs **predictable and parseable** — critical when building pipelines or creating reusable templates. Constraints also force the model to be concise, eliminating filler and padding that reduces output quality.


---

## ④ Common Mistakes & Fixes
*What beginners get wrong — and how to correct it.*

> [!WARNING] ⚠️
> These are the six mistakes that appear most often in students' first attempts at prompting. Each one has a clear, teachable fix.

| # | Mistake | Why It Fails | Fix |
|---|---|---|---|
| **01** | **Vague instructions**<br/>*"Write something good"* | The model has no constraints to anchor its interpretation. | **Specify audience, length, tone, and purpose.** |
| **02** | **Overloading one prompt**<br/>*5 unrelated tasks in one message* | The model may miss parts, blend them together, or prioritise unevenly. | **Break complex tasks into separate, sequential prompts.** |
| **03** | **No context provided**<br/>*"Help me write an email"*| The model doesn't know who you are, who the email is for, or why. | **Add: who is sending, to whom, for what purpose.** |
| **04** | **Asking for opinions as facts**<br/>*"What's the best Python framework?"* | The model will hallucinate a "correct" answer to a subjective question. | **Ask: "What are the trade-offs of Django vs Flask for my use case?"** |
| **05** | **No output format specified**<br/>*Expecting a table, getting paragraphs* | The model defaults to paragraph form unless instructed otherwise. | **Explicitly say: "Respond as a markdown table with columns X, Y, Z."** |
| **06** | **Not iterating**<br/>*Giving up after one bad output* | Prompting is a dialogue, not a one-shot transaction. | **Refine: identify which part failed, adjust that element, retry.** |

---

## ⑤ Mini Lesson Plans
*How I would teach these concepts to real students.*

### 🎓 Lesson 1: Introduction to Prompting
_⏱ 45 min_ | _👥 Beginner_

1. **Hook (5 min)**: Show the same task with a vague vs specific prompt — let students see the output difference first-hand. Ask: "What changed?"
2. **Concept (10 min)**: Explain the 4 core elements of a strong prompt: Role, Task, Context, and Format. Use a simple 2×2 visual.
3. **Practice (20 min)**: Students rewrite 3 weak prompts using the framework. Share and discuss results as a group.
4. **Reflection (10 min)**: Each student writes one insight: "The most important thing I'll change about how I prompt is…"

### 🎓 Lesson 2: Few-Shot & Chain-of-Thought
_⏱ 60 min_ | _👥 Intermediate_

1. **Real Problem Setup (10 min)**: Present a real classification task: sorting 20 customer reviews into categories. Students attempt it with a basic prompt.
2. **Introduce Few-Shot (15 min)**: Teach the pattern: Example → Example → Example → Task. Students rebuild their prompt using 3 examples. Compare outputs.
3. **Introduce Chain-of-Thought (15 min)**: Use a word problem. Show how adding "think step by step" changes the model's reasoning path and accuracy.
4. **Pair Challenge (20 min)**: In pairs: solve a complex 3-step problem using CoT. One person prompts, one observes and critiques. Switch roles.

### 🎓 Lesson 3: Prompt Design for Real Work
_⏱ 90 min_ | _👥 All Levels_

1. **Use Case Gallery (20 min)**: Students browse 6 real-world use cases (email writing, data summarisation, code review, lesson planning, translation, brainstorming). Pick one.
2. **Build Your Prompt Template (30 min)**: Students design a reusable prompt template for their chosen use case, using all techniques learned. Must include role, context, task, and format.
3. **Test & Iterate (20 min)**: Run the template 3 times with varied inputs. Document what breaks, what works, and what they changed each time.
4. **Present & Peer Review (20 min)**: Each student presents their template + one key learning. Peers give structured feedback: one strength, one suggestion.

---

## ⑥ Capstone Challenge
*A complex real-world task solved with advanced prompting with full reasoning documented.*

> [!IMPORTANT] 🏆 Challenge
> Create a multi-step prompt system that takes a raw interview transcript and produces a structured job candidate evaluation — without human editing of the output.

### ⚡ Advanced Prompt · Capstone Solution
**Interview Transcript → Candidate Evaluation**

This prompt chain uses role assignment, structured output, chain-of-thought reasoning, and constraint-setting across two sequential calls.

**PROMPT 1 — Extract & Structure**
```text
You are an expert HR analyst with 10+ years evaluating technical candidates.

Given the interview transcript below, extract and structure the following:
- Key technical skills mentioned (with evidence from transcript)
- Communication quality (score 1–5 with one-sentence justification)
- Problem-solving indicators (specific examples from the interview)
- Red flags, if any

Think through each category carefully before writing your analysis.
Do not add information not present in the transcript.

[TRANSCRIPT]
```

**PROMPT 2 — Synthesise & Recommend**
```text
Using the structured analysis above, produce a final candidate report:

**Overall Rating:** [Strong Yes / Yes / Maybe / No] 
**Top 3 Strengths:** (one sentence each)
**Top 2 Concerns:** (one sentence each)
**Recommendation:** (2–3 sentences max, plain language)

Be direct. Avoid hedging language. This report will go to a hiring manager.
```

> [!NOTE] 📝 Reasoning
> Splitting into two prompts prevents the model from skipping the analysis phase and jumping to a conclusion. Prompt 1 forces evidence-based extraction; Prompt 2 synthesises from a constrained, structured input — increasing reliability and reducing hallucination.

<br>

> [!TIP] ✅ Playbook Complete
> This playbook covers the foundational and intermediate skills expected of an AI Prompt Engineering Tutor. All examples are original, all techniques are explained from first principles, and the lesson plans are ready to adapt for real students.