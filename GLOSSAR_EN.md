# Glossary: AI Engineering

## A

### A2A (Agent2Agent)

A protocol for communication between independent agents, including across organizational boundaries. Agents advertise what they can do and delegate tasks to one another.

**Context:** Complements MCP rather than replacing it. Rough split: MCP connects an agent to tools, A2A connects agents to each other. Security-wise the hardest of the three cases, because trust and permissions have to be established across a foreign organization.

**Sources:** [ACP vs MCP vs A2A, comparison](https://www.morphllm.com/comparisons/acp-vs-mcp-vs-a2a)

### ACP (Agent Client Protocol)

A protocol for the connection between an agent and its working environment, usually an editor or IDE. It governs how the agent sees files, proposes changes, and receives feedback.

**Context:** The acronym is doubly assigned. It stands both for Agent Client Protocol and for Agent Communication Protocol, a REST-based method for coordinating several agents within one organization. Clarify which one is meant before the discussion. Both are far less widespread than MCP.

**Sources:** [ACP vs MCP vs A2A, comparison](https://www.morphllm.com/comparisons/acp-vs-mcp-vs-a2a)

### Agent

A language model in a loop with tools. It receives a task, decides on the next step, calls a tool, looks at the result, and repeats that until the task is done or a limit kicks in.

**Context:** The most overstretched term in the field. Much of what is sold as an agent is a fixed sequence of model calls with no decision of its own about the next step. The useful test question: does the system itself decide when to stop?

**Sources:** [Building effective agents, Anthropic](https://www.anthropic.com/engineering/building-effective-agents)

### Agentic Workflow

A process in which a model decides the next step itself across several steps, as opposed to a hard-wired chain of calls.

**Context:** An umbrella term with soft edges. Agent names the component, Agentic Workflow the process. The dividing line from Workflow runs along the question of who decides the next step.

**Sources:** [Building effective agents, Anthropic](https://www.anthropic.com/engineering/building-effective-agents)

### AGENTS.md and CLAUDE.md

Text files in the project directory that permanently tell a coding agent what it should know about the project: structure, commands, conventions, and things it should avoid. Their content moves into the context at the start of each session.

**Context:** AGENTS.md is the tool-agnostic format, now under the umbrella of the Linux Foundation and used in tens of thousands of repositories. CLAUDE.md is the native and richer format of Claude Code, which additionally reads AGENTS.md. Two practical points: the content costs context in every session, so short beats complete. And the file comes from the repository, making it an input like any other and thus a possible carrier for prompt injection in foreign or shared projects.

**Sources:** [AGENTS.md spec and comparison to CLAUDE.md](https://www.morphllm.com/agents-md-guide)

## C

### Chunking

Documents are split into smaller pieces so they can be indexed, searched, and loaded into the context individually. Size and cut points determine which connections are preserved.

**Context:** The most inconspicuous lever in RAG systems, and often the most effective. A cut through the middle of a table or a condition makes the hit worthless without the retrieval result looking bad.

**Sources:** [Guide to Chunking Strategies for RAG, Zilliz](https://zilliz.com/learn/guide-to-chunking-strategies-for-rag)

### Computer Use

The model operates a graphical interface by reading screenshots and producing mouse and keyboard input. Intended for systems that offer no API.

**Context:** The broadest attack surface among the tool types, because the screen content itself can carry instructions and arbitrary foreign content ends up on it. Also slow, expensive, and sensitive to layout changes, something test automation has known for decades.

### Confused Deputy

A component with permissions is induced by someone without those permissions to use its authority on their behalf. The term goes back to Norm Hardy, 1988, making it considerably older than language models.

**Context:** The most precise description of why prompt injection is dangerous at all. An agent carries the user's rights and executes instructions from untrusted material. The problem is the delegated rights, not the text.

**Sources:** [Confused deputy problem, Wikipedia](https://en.wikipedia.org/wiki/Confused_deputy_problem)

### Context Engineering

The design of what ends up in the Context Window. A model can only judge information it receives, which is why better selection often helps more than a better model. This includes RAG, Memory, compression, Chunking, ranking, the choice of conversation history, and feeding tool results back in.

**Context:** The term emphasizes the selection of the information a model receives, not its phrasing. That sets it apart from Prompt Engineering, which operates on the phrasing of the individual call.

**Sources:** [Effective context engineering for AI agents, Anthropic](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)

### Context Poisoning

Untrusted content enters the Context Window and influences all subsequent decisions. Sources are retrieved documents, tool results, web pages, files in the project, or a persistent Memory store.

**Context:** Used inconsistently and overlaps with Prompt Injection. A useful distinction: Prompt Injection describes the injected instruction, Context Poisoning the state afterward, in which the false information keeps taking effect. With persistent storage it survives the session, which is then called Memory Poisoning.

**Sources:** [Poison everywhere: No output from your MCP server is safe, CyberArk](https://www.cyberark.com/resources/threat-research-blog/poison-everywhere-no-output-from-your-mcp-server-is-safe)

### Context Rot

As input length grows, accuracy drops long before the Context Window is exhausted. Causes are the uneven attention across position, dilution with many tokens, and similar-sounding but irrelevant content.

**Context:** The 2025 Chroma study shows the effect across 18 frontier models. Practical consequence: the advertised window size is not a usable working size. Anyone running long contexts should measure their own limit instead of taking it from the spec sheet.

**Sources:** [Context Rot, Chroma Research](https://www.trychroma.com/research/context-rot)

### Context Window

The maximum amount of tokens a model can process at once in a single call. Everything that should feed into the answer has to fit: system prompt, history, retrieved documents, tool results.

**Context:** A large window does not replace selection. Accuracy drops noticeably well before the upper limit, see Context Rot. One sub-effect of this is Lost in the Middle: models attend to the start and end of the input more reliably than the middle.

**Sources:** [Effective context engineering for AI agents, Anthropic](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)

## D

### Determinism and Reproducibility

Determinism means: same input, same output. Reproducibility means: a run can be traceably repeated later, including model version, parameters, and inputs.

**Context:** Both are weaker with LLMs than testing experience from classic software would suggest. Even at temperature 0, the order of floating-point operations on the GPU, batching, and routing in Mixture-of-Experts models lead to differing outputs. For testing this means: check for properties instead of character-for-character equality, and run multiple times.

**Sources:** [Reproducibility, vLLM documentation](https://docs.vllm.ai/en/v0.9.1/usage/reproducibility.html)

### Distillation

A large model serves as a teacher for a smaller one that imitates its behavior. The result is a cheaper and faster model with narrower ability.

**Context:** The usual route to small models that come close to large ones on a single task. The loss shows at the edges, that is, with unusual inputs missing from the teaching material.

**Sources:** [Distilling the Knowledge in a Neural Network, original paper 2015](https://arxiv.org/abs/1503.02531)

## E

### Embedding

A text is translated into a vector of numbers whose position in space reflects semantic similarity. The basis of Vector Search.

**Context:** Similarity is neither relevance nor truth. Two opposite statements often lie close together because they are about the same topic. Practically important: switching the embedding model fully invalidates an existing index; the whole corpus has to be recomputed.

### Eval

A repeatable measurement of system quality against a fixed set of cases with a known expected value. The result is a metric over time, not a single yes/no verdict.

**Context:** The term covers very different things, from a handful of examples to full-blown benchmarks. When reading other people's eval results, it always pays to ask who wrote the test cases.

**Sources:** [OpenAI Evals, framework and examples](https://github.com/openai/evals)

### Eval Harness

The infrastructure that runs an eval: load test cases, call the model, collect outputs, apply the scoring, store results, and keep them comparable over time.

**Context:** To be distinguished from the agent harness. One runs the system in operation, the other runs measurements on it. Same word stem, different thing. The OpenAI incident in July 2026 took place in an eval harness.

**Sources:** [OpenAI Evals, framework and examples](https://github.com/openai/evals)

### Excessive Agency

A system is allowed to do more than its task requires: too many tools, too broad permissions, too few confirmation steps. Listed in the OWASP list as LLM06.

**Context:** The most common self-inflicted vulnerability, because broad permissions make development more convenient and nobody takes them back later. Useful test question: which action could this system trigger that cannot be undone?

**Sources:** [OWASP Top 10 for LLM Applications 2025, PDF](https://owasp.org/www-project-top-10-for-large-language-model-applications/assets/PDF/OWASP-Top-10-for-LLMs-v2025.pdf)

## F

### Fine-Tuning

A pre-trained model is trained further on your own examples to shape format, tone, or domain behavior.

**Context:** Good for form and behavior, weak for knowledge. Anyone wanting to keep facts current is better off with RAG, because a document can be swapped out and a weight cannot. Every fine-tuning also produces its own artifact that wants to be versioned, tested, and maintained.

**Sources:** [RAG vs. Fine-tuning, IBM](https://www.ibm.com/think/topics/rag-vs-fine-tuning)

### Forward Engineering

In the original sense, the direction from requirements and design to a working implementation, that is, the counterpart to reverse engineering. In the AI context, extended to building AI-native applications out of business requirements, as opposed to modernizing existing ones.

**Context:** Careful. In the AI context the term is occasionally reinterpreted as an overarching layer above the whole of systems development, which blurs its original meaning – the counterpart to reverse engineering. On top of that comes the risk of confusion with Forward Deployed Engineering, a prominent term in 2026 with a different meaning: developers who sit with the customer and ship there.

**Sources:** [What Is Forward Engineering](https://luvina.net/forward-engineering/) · [What is Forward Deployed Engineering](https://invisibletech.ai/blog/what-is-forward-deployed-engineering)

## G

### Grounding

The output is tied to verifiable sources instead of being produced from the model's memory alone. Common implementations are RAG, search integration, Knowledge Graphs, and tool calls, often combined with a citation per statement.

**Context:** Grounding lowers the rate of fabricated content, it does not eliminate it. A model can summarize a correctly retrieved source incorrectly. The result only becomes checkable once every statement points to a concrete location.

**Sources:** [LLM Grounding, glossary entry](https://www.iguazio.com/glossary/llm-grounding/)

### Guardrail

A control that inspects inputs or outputs and blocks, filters, or redirects them. Common ones are input filters against prompt injection, output filters against data exfiltration, and hard limits for permissions and budgets.

**Context:** Guardrails sit on several layers at once, not just in the Harness. A guardrail phrased as an instruction in the prompt is a request to the model.

**Sources:** [OWASP Top 10 for LLM Applications 2025, PDF](https://owasp.org/www-project-top-10-for-large-language-model-applications/assets/PDF/OWASP-Top-10-for-LLMs-v2025.pdf)

## H

### Hallucination

The model produces fluent, plausible-sounding content that is false or not supported by the available sources. Fabricated citations, statutes, libraries, and people are the most common forms.

**Context:** The word suggests a malfunction. In fact it is the normal behavior of a system that produces likely continuations. From the model's point of view there is no difference between a correct and a fabricated answer, which is why the behavior can be limited and measured but not repaired away. Listed in the OWASP list as LLM09 Misinformation.

**Sources:** [Hallucination (artificial intelligence), Wikipedia](https://en.wikipedia.org/wiki/Hallucination_\(artificial_intelligence\))

### Harness

The deterministic runtime layer around the model. It checks, authorizes, executes, and logs every action the model proposes, against schemas, permissions, budgets, and security rules.

**Context:** The most interesting layer for quality assurance, because this is where the boundaries are actually enforced. What is in the prompt is a request. What is in the harness is a rule.

**Sources:** [Harness Engineering, Faros](https://www.faros.ai/blog/harness-engineering)

### Harness Engineering

The design of the runtime environment around the model. Production AI applications rarely produce only text; they run code, call tools, search the web, and check results. This includes Tool Calling, MCP, code execution, browser automation, Sub-Agents, verification, retry strategies, error handling, and Guardrails.

**Context:** In broad circulation since 2026, usually summarized as "Agent = model + harness". The boundary between Harness and Loop is drawn inconsistently, especially around verification.

**Sources:** [Harness Engineering, Faros](https://www.faros.ai/blog/harness-engineering) · [Harness Engineering for AI Coding Agents, Augment Code](https://www.augmentcode.com/guides/harness-engineering-ai-coding-agents)

### Human in the Loop

A human confirms, corrects, or blocks at defined points before the system continues.

**Context:** Effective against wrong decisions and useless once nobody is looking anymore. Two traps: approval fatigue, where confirmation becomes reflexive, and speed, because in processes that must react to attacks, the wait for a human is itself a risk. The pattern becomes viable when it is decided in advance which actions need a signature, rather than all of them.

**Sources:** [OWASP Top 10 for LLM Applications 2025, PDF](https://owasp.org/www-project-top-10-for-large-language-model-applications/assets/PDF/OWASP-Top-10-for-LLMs-v2025.pdf)

## J

### Jailbreak

An input that makes a model bypass the behavioral limits it was trained with. Common patterns are role-play, hypothetical framing, encoding, and flooding the context with examples.

**Context:** Often lumped together with Prompt Injection. The jailbreak targets the model's policy, prompt injection targets the application's instruction hierarchy. Different targets, different countermeasures.

**Sources:** [OWASP LLM Top 10, overview at Promptfoo](https://www.promptfoo.dev/docs/red-team/owasp-llm-top-10/)

## K

### Knowledge Graph

Knowledge is stored as nodes and named relationships rather than as prose. Queries follow the edges, which makes multi-step questions answerable.

**Context:** Strong where relationships are the actual information: responsibilities, dependencies, permissions, supply chains. The effort lies in modeling and maintenance, not in querying, which is why such projects fail on organization rather than technology.

## L

### LangChain

A framework for building LLM applications. It provides building blocks for model calls, prompts, tool integration, and retrieval, and unifies the interfaces of different providers.

**Context:** The best-known representative of its kind and correspondingly polarizing. The abstraction layer saves work at the start and complicates debugging later, because several layers sit between your own code and the model call. For simple cases the model provider's SDK is often enough.

**Sources:** [LangChain vs LangGraph vs LangSmith, comparison](https://www.truefoundry.com/blog/langchain-vs-langgraph-vs-langsmith)

### Langfuse

An open, self-hostable platform for tracing and evaluation of LLM applications, independent of the framework used.

**Context:** The usual alternative to LangSmith when the data must not leave your own network. In the German environment often exactly the deciding criterion.

**Sources:** [langfuse.com](https://langfuse.com/)

### LangGraph

An extension on top of LangChain for stateful processes. The process is described as a graph, with state management, checkpoints, branching, and stopping points for human approvals.

**Context:** Covers exactly what is described here under Orchestration and Loop Engineering. The graph makes processes checkable and shifts the complexity into the graph definition.

**Sources:** [LangChain vs LangGraph vs LangSmith, comparison](https://www.truefoundry.com/blog/langchain-vs-langgraph-vs-langsmith)

### LangSmith

The commercial platform from the same provider for tracing, evaluation, and monitoring of LLM applications. Via OpenTelemetry now usable for applications outside LangChain as well.

**Sources:** [LangChain vs LangGraph vs LangSmith, comparison](https://www.truefoundry.com/blog/langchain-vs-langgraph-vs-langsmith)

### Lethal Trifecta

Three properties that together enable the exfiltration of confidential data: access to confidential data, processing of untrusted content, and the ability to communicate outward. The term goes back to Simon Willison, June 2025.

**Context:** The most useful quick check for agent architectures. Two of the three properties are manageable. Removing any one of the three removes the entire class of attack, and the outbound channel is usually the easiest to close.

**Sources:** [The lethal trifecta for AI agents, Simon Willison](https://simonwillison.net/2025/Jun/16/the-lethal-trifecta/)

### LLM-as-a-Judge

A model evaluates the output of another model against criteria in natural language. Common where there is no unambiguously correct answer.

**Context:** The judge is itself a measuring instrument with errors and bias. Without calibration against human judgments, its result is an opinion with decimal places.

**Sources:** [Judging LLM-as-a-Judge, original paper 2023](https://arxiv.org/abs/2306.05685)

### Loop Engineering

The design of the question of when an agent continues, restarts, or stops. Complex tasks need several passes rather than a single call. This includes planning, reflection, self-correction, stopping conditions, iteration limits, and budgets for time, cost, and tokens.

**Context:** A comparatively young term, but established enough that providers like IBM maintain their own definitions. The stopping condition is the part that is most often missing in practice.

**Sources:** [What Is Loop Engineering, IBM](https://www.ibm.com/think/topics/loop-engineering)

## M

### MCP (Model Context Protocol)

An open protocol through which models are connected uniformly to tools, data sources, and prompts. It standardizes how a client describes available tools to a model and handles their calls.

**Context:** MCP is an implementation of Tool Calling, not a separate concept alongside it. Relevant from a security perspective because an MCP server shifts a trust boundary. There is now a dedicated OWASP list for it. MCP comes from Anthropic and is by far the most widespread of the agent protocols. For the distinction from ACP and A2A, see those entries.

**Sources:** [modelcontextprotocol.io](https://modelcontextprotocol.io/) · [OWASP MCP Top 10](https://owasp.org/www-project-mcp-top-10/)

### Memory

Storage that persists beyond a single session: facts about the user, earlier decisions, work in progress. Technically usually a file or a vector store from which content is loaded on demand.

**Context:** Memory is Context Engineering with persistence, not model memory. Security-relevant because a piece of false information, once injected, survives the session. What gets written into it deserves the same scrutiny as an input.

**Sources:** [Effective context engineering for AI agents, Anthropic](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)

### Model Drift and Upgrade Regression

An application's behavior changes without its code changing, because the provider updates or replaces the model. Prompts that reliably held before suddenly deliver different results.

**Context:** Model Drift comes from classic machine learning, where it means changed input data over time. In the LLM context the same term is used for the model change itself, so when reading, clarify which meaning is intended. From a QA point of view the strongest reason to run evals at all: without them nobody notices the difference.

### Model Routing

Requests are routed to different models depending on the task, simple ones to a small and fast model, hard ones to a large one.

**Context:** Saves cost and latency and creates a new testing question. The application's behavior now depends on which path the router chooses, so the router needs its own test cases.

### Model Supply Chain

The chain of model weights, training and fine-tuning data, adapters, libraries, and tool servers from which an AI application is assembled. Each station is a source with its own trust problem.

**Context:** Weights are binary files from a foreign hand, and some serialization formats execute code on load. Listed in the OWASP list as LLM03. The Hugging Face incident in July 2026 began in the data processing pipeline, not in the model, which shows the breadth of this attack surface.

**Sources:** [OWASP Top 10 for LLM Applications 2025, PDF](https://owasp.org/www-project-top-10-for-large-language-model-applications/assets/PDF/OWASP-Top-10-for-LLMs-v2025.pdf) · [Security incident disclosure, Hugging Face](https://huggingface.co/blog/security-incident-july-2026)

### Multi-Agent System

Several agents work on the same task, either as equals or under a coordinating agent.

**Context:** Sounds like division of labor, but costs context, latency, and traceability. Often a single agent with better tools solves the same task. Security-relevant because permissions can add up unnoticed across agent boundaries.

**Sources:** [Building effective agents, Anthropic](https://www.anthropic.com/engineering/building-effective-agents)

## O

### Observability and Tracing

Recording of what a system actually did: prompts, model responses, tool calls, intermediate steps, latencies, costs. A trace chains these events into a traceable run.

**Context:** With non-deterministic systems, the recording replaces repeatability. Without a trace, a bug report is worthless because the run cannot be reconstructed. Delicate from a data-protection standpoint, because a complete trace contains all inputs. For standardization there are the GenAI Semantic Conventions from OpenTelemetry, still in draft as of mid-2026.

**Sources:** [OpenTelemetry GenAI Semantic Conventions](https://mlflow.org/docs/latest/genai/tracing/opentelemetry/genai-semconv/)

### Open Weight and Open Source

Open Weight means: the weights are available for download and can be run locally. Open Source in the strict sense additionally requires open training data, open training code, and a license without usage restrictions.

**Context:** Most models advertised as Open Source are Open Weight with conditions. For practice, what mostly counts is whether you may run them on your own hardware. In forensics with confidential data that is exactly what tips the scale, because neither data nor credentials leave your own network.

**Sources:** [Open Source AI Definition, Open Source Initiative](https://opensource.org/ai)

### Orchestration

The control of several steps, models, and tools into one process, including order, parallelism, state management, and error handling.

**Context:** Often confused with Agent. Orchestration fixes the process in advance, an agent decides it at runtime. Most production systems are hybrids of both.

**Sources:** [Building effective agents, Anthropic](https://www.anthropic.com/engineering/building-effective-agents)

### Orchestrator Agent

The lead agent in the orchestrator-workers pattern. It breaks down the task, assigns clearly scoped subtasks to Sub-Agents, collects their results, and decides on the next step. Anthropic calls it Lead Agent in its research architecture.

**Context:** To be distinguished from Orchestration: there the process is in the code, here a model decides at runtime. The workers do not talk to each other; every decision about the next step lies with the orchestrator. The pattern is worthwhile when the subtasks are unknown in advance. If they are known, you pay context, latency, and traceability with no return.

**Sources:** [How we built our multi-agent research system, Anthropic](https://www.anthropic.com/engineering/multi-agent-research-system) · [Orchestrator-Workers, Anthropic Cookbook](https://github.com/anthropics/anthropic-cookbook/blob/main/patterns/agents/orchestrator_workers.ipynb)

## P

### Prompt

The entire text a model receives for a call. In practice it is composed of system prompt, tool descriptions, conversation history, retrieved content, and the current input.

**Context:** Colloquially, prompt often means only the user input. Technically it is everything the model sees. The difference becomes apparent at the latest when cost, latency, or window limits come up.

**Sources:** [Prompt Engineering Overview, Anthropic](https://docs.claude.com/en/docs/build-with-claude/prompt-engineering/overview)

### Prompt Caching

Recurring parts of a prompt, such as system prompt and tool descriptions, are cached at the provider and processed more cheaply and faster on subsequent calls.

**Context:** Only takes effect on an unchanged prefix. A change at the start invalidates the cache for everything after it, which is why variable content belongs at the end. For agents that send the same preamble hundreds of times, the single largest cost lever.

### Prompt Engineering

The design of a single model call. This includes role assignment, instructions and constraints, examples in the prompt (few-shot), enforced output formats like JSON, and reusable prompt templates.

**Context:** One of the older terms in the field and the one most often mistaken for the whole: Prompt Engineering is often equated with the entire work on AI systems. It does not lose importance, but becomes only a part of something larger.

**Sources:** [Prompt Engineering Overview, Anthropic](https://docs.claude.com/en/docs/build-with-claude/prompt-engineering/overview)

### Prompt Injection

Attacker-controlled text makes the model follow instructions the operator never intended. Direct means: the user writes them into the input themselves. Indirect means: they sit in content the model reads as part of its work, for example in a web page, an email, a PDF, a file in the repository, or a tool result.

**Context:** Number one of the OWASP Top 10 for LLM applications and without a general solution, because instructions and data share the same channel. Filters lower the hit rate, they do not eliminate the class. The workable design assumption is: any content the model reads can contain instructions. The indirect variant is the more dangerous, because the attacker needs no access to the application.

**Sources:** [OWASP Top 10 for LLM Applications 2025, PDF](https://owasp.org/www-project-top-10-for-large-language-model-applications/assets/PDF/OWASP-Top-10-for-LLMs-v2025.pdf) · [Prompt Injection, article series by Simon Willison](https://simonwillison.net/tags/prompt-injection/)

## R

### RAG (Retrieval Augmented Generation)

External knowledge is retrieved at runtime and placed into the prompt instead of being trained into the model. Typical is a vector search over chunked documents followed by a selection of the best hits.

**Context:** Quality stands and falls with the retrieval, not with the model. When testing, it pays to evaluate the two separately.

**Sources:** [Retrieval-Augmented Generation, original paper 2020](https://arxiv.org/abs/2005.11401)

### Reasoning Model

A model that produces a longer internal derivation before the answer and spends more compute on it. Strong at multi-step tasks, math, and code.

**Context:** More expensive and slower, and the internal derivation is usually shortened or not visible at all. It is also not a reliable explanation of how the answer came about, so it does not serve as proof to an auditor.

### Red Team and Blue Team

The red team attacks to find weaknesses, the blue team defends and detects. For AI systems, red teaming additionally includes the systematic elicitation of undesired model behavior before release.

**Context:** Both sides are currently shifting to agents, and this creates an imbalance. The attacking agent system is bound by no usage policy and asks no one. The defending one hangs on its provider's guardrails and on release steps. At equal capability, the clock rate decides.

**Sources:** [Security incident disclosure, Hugging Face](https://huggingface.co/blog/security-incident-july-2026)

### Reranking

After the first search, a second, more precise model re-sorts the hits before the best ones move into the context.

**Context:** Often rescues systems whose vector search hits too coarsely. Costs latency and an additional model call. When measuring, it pays to look at the recall of the search and the precision of the reranker separately.

## S

### Sandbox and Containment

The sandbox limits what code executed at the model's behest can reach: file system, network, credentials, compute and time budget. Containment is the higher-level property that actions do not leave the intended boundary.

**Context:** A sandbox is only as strong as its most generous permitted exit. In the OpenAI and Hugging Face incident in July 2026, a single approved package proxy was enough to get from a supposedly isolated environment onto the open internet.

**Sources:** [OpenAI on the incident](https://openai.com/index/hugging-face-model-evaluation-security-incident/) · [Technical timeline, Hugging Face](https://huggingface.co/blog/agent-intrusion-technical-timeline)

### Sandboxed Code Execution

Code produced by the model is executed, but in a sealed-off environment with limited access to file system, network, credentials, and runtime.

**Context:** The standard way to allow code execution at all, and at the same time the place where containment usually fails. The escape route is rarely the sandbox itself, but a deliberately approved exit like a package proxy or a registry mirror.

**Sources:** [OpenAI on the incident](https://openai.com/index/hugging-face-model-evaluation-security-incident/)

### Skill

A packaged bundle of instructions and optionally scripts or resources that a model loads on demand to accomplish a certain kind of task.

**Context:** Anthropic runs the concept as Agent Skills, a folder of instructions, scripts, and resources that Claude loads itself when the occasion fits. Easily confused with a tool or a prompt template. The distinguishing feature is the conditional on-demand load, which is why a Skill is primarily a means of Context Engineering. As soon as executable scripts are part of it, it reaches into the Harness.

**Sources:** [Agent Skills, Claude Platform Docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) · [Open skills collection, Anthropic](https://github.com/anthropics/skills)

### Structured Output

The model is bound to a fixed output format, usually JSON against a schema. Implemented either through constrained decoding or through downstream validation with retry.

**Context:** Schema conformance is not factual correctness. A valid JSON can contain wrong values. The real gain is that the output can be processed automatically and thus checked automatically at all.

### Sub-Agent

A separate agent with its own context to which a superordinate agent hands off a subtask. It returns a result without bringing along its entire work history.

**Context:** Useful for relieving the Context Window, because the sub-agent works in a fresh context and returns only the result. The price is that the superordinate agent sees only the summary and notices detailed errors less easily. Its counterpart is the Orchestrator Agent, called Lead Agent at Anthropic.

**Sources:** [Building effective agents, Anthropic](https://www.anthropic.com/engineering/building-effective-agents)

### System Prompt

The instructions that precede the actual conversation and set role, rules, tone, and available tools. They apply across all turns and come from the operator of the application, not the user.

**Context:** Not a security boundary. The system prompt lies in the same Context Window as everything else and competes with later text for attention. It can usually be read out, so secrets do not belong in it. Listed in the OWASP list as LLM07 System Prompt Leakage.

**Sources:** [OWASP Top 10 for LLM Applications 2025, PDF](https://owasp.org/www-project-top-10-for-large-language-model-applications/assets/PDF/OWASP-Top-10-for-LLMs-v2025.pdf)

## T

### Temperature and Seed

Temperature scales the probability distribution before the next token is drawn. Low values make the choice more predictable, high values more varied. The seed sets the starting value of the random generator during sampling.

**Context:** At temperature 0 the most probable token is always chosen computationally, which makes the seed ineffective. That still does not guarantee an identical output, see Determinism and Reproducibility. Also, not all providers offer a seed.

**Sources:** [Controlling randomness in LLMs: Temperature and Seed](https://dylancastillo.co/posts/seed-temperature-llms.html)

### Token

The smallest unit into which text is split before a model processes it. A token roughly corresponds to a word fragment.

**Context:** Cost, latency, and the limit of the Context Window all count in tokens, not in characters or words. German texts need noticeably more tokens than English for the same content, which shifts budgets and window limits.

**Sources:** [Tokenizer to try, OpenAI](https://platform.openai.com/tokenizer)

### Token Budget

An upper limit for tokens per call, per run, or per period. Serves cost control and at the same time as a stopping condition against endless loops.

**Context:** One of the few limits that can be hard-enforced, because it makes no assumptions about content. It therefore belongs in the Harness and not in the prompt.

### Tool Calling

Instead of text, the model emits a structured call that the surrounding software executes. The result comes back into the context as new information.

**Context:** The model calls nothing, it proposes a call. Who executes, and with what permissions, is an architectural decision.

**Sources:** [Building effective agents, Anthropic](https://www.anthropic.com/engineering/building-effective-agents)

### Tool Poisoning

Malicious instructions sit in the descriptions of tools, that is, in names, documentation, and parameter descriptions that the model reads as part of its context. Relevant everywhere tool definitions come from foreign servers.

**Context:** Effective because tool descriptions are practically never read and reviewed. On top of that, a server can change its descriptions after approval, which is called a Rug Pull. As a countermeasure it helps to freeze the definition after review.

**Sources:** [MCP03:2025 Tool Poisoning, OWASP](https://owasp.org/www-project-mcp-top-10/2025/MCP03-2025%E2%80%93Tool-Poisoning) · [Reproducible examples, Invariant Labs](https://github.com/invariantlabs-ai/mcp-injection-experiments)

## V

### Vector Search

Search over embeddings: the query is translated into the same vector space, then the nearest entries are returned.

**Context:** Finds the similar, not the correct. For exact identifiers, version numbers, error codes, and technical terms, classic full-text search regularly beats it, which is why hybrid methods combining both are common today.

**Sources:** [Why Vector Search Alone Isn't Enough, InfoQ](https://www.infoq.com/articles/vector-search-hybrid-retrieval-rag/)

### Vibe Coding

Programming by describing: you describe in natural language what should come about, take over the generated code largely unread, and steer via further descriptions. The term goes back to Andrej Karpathy, February 2025.

**Context:** A viable way of working for throwaway work, prototypes, and exploration. The point that defines the method is the omitted review step, and that is exactly what decides whether the result may go to production. The term is now often used simply for "developing with AI support", which makes it useless.

**Sources:** [Vibe coding, Wikipedia](https://en.wikipedia.org/wiki/Vibe_coding)

## W

### Workflow

A fixed sequence of steps in which order and branching are in the code. Model calls are individual stations within it.

**Context:** The counter-term to Agentic Workflow. A workflow is predictable, checkable, and boring, which in production are three advantages. Many systems sold as agentic are workflows, and most of the time that is the right choice.

**Sources:** [Building effective agents, Anthropic](https://www.anthropic.com/engineering/building-effective-agents)
