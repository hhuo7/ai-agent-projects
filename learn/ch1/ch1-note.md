
## Experiment Background:

Downloaded chapter1/ from the GitHub repository for Understanding AI Agents: Design Principles and Engineering Practice.

Conducted context ablation experiments to verify how context functions as the "eyes" of an Agent, the structure of context and the role of each component, as well as the Agent's response when specific components are missing.

## Experimental Steps:

Download Code from Repository:

https://github.com/bojieli/ai-agent-book/chapter1/context

Configure Environment:

\chapter1\context\.venv

I selected the DeepSeek model.

Note: Watch out for a potential pitfall here—the code only supports Python 3.13 and lower.

Execute Ablation Experiments Step-by-Step:

The code includes five experiments; I ran the "Currency Conversion and Average Calculation" experiment.
<img width="837" height="535" alt="image" src="https://github.com/user-attachments/assets/3e979385-83a8-42ab-9234-f8e942e3676e" />

There is 1 control group and 4 experimental (ablation) groups:

Control Group:

full: Full context mode.

Experimental Groups:

no_history: Context with message history removed.

no_tool_calls: Context with the tool list removed.

no_tool_results: Context with tool execution results removed.

no_reasoning: Context with the reasoning process removed.

## Experiment Conclusion

LLMs natively possess strong reasoning capabilities, but it is precisely this reasoning capability that gives rise to non-fact-based hallucinations. What makes it particularly tricky is that the model outputs these results to you with answers that are nearly correct, making them highly misleading.

For example, in the no_tool_calls mode where the tool list (tool_calls) was set to empty, the Agent invoked the LLM once. During this single call, the LLM went through 5 iterations of reasoning—self-doubt, overriding its own steps, and retrying. When no tool results were forthcoming, it actually outputted a final answer based purely on its own assumptions about the task. This result was slightly different from the output generated through actual tool calls (due to exchange rate discrepancies), yet it looked remarkably convincing.

Conclusion: Whenever a task involves precise calculations, strict rules, or authoritative databases, you must route it to dedicated tools for processing. Never rely solely on an LLM's internal calculations!






