---
marp: true
theme: local-ai
paginate: true
size: 16:9
html: true
title: Local AI, explained with food
description: A short guide to why local AI matters and the terms used to describe it
author: Yingjie Soon
---

<!-- _class: hero -->
<!-- _paginate: false -->

![bg](assets/01-cookbook-counter-v4.png)
<img class="hero-logo" src="assets/00-abc-logo-v2.png" alt="Agentic Builders Collective">

# Local AI,<br>explained with food

<!--
Timing: 40 seconds.

Most of us already know cloud AI. You send a request to somebody else's computers and get an answer back. Tonight, people will talk about running models on hardware you control. I want to give you enough vocabulary to follow the rest of the evening.

I will use one dinner setup throughout: the model is the cookbook, the runtime is the cook doing the work, and memory is the counter space everything has to share.

[Sources]
- Agentic Builders Collective logo supplied by the organiser.
- Cookbook-counter artwork generated on 14 September 2026 with character references from https://github.com/tinkertanker/tkrobot-stickers.
-->

---

<!-- _class: why-local-slide -->

# Why cook for yourself?

<div class="why-intro">Local AI runs the model on hardware you control.</div>

<div class="why-points">
  <p><strong>No bill for every serving</strong><span>Repeated work without a per-token API bill.</span></p>
  <p><strong>Private ingredients stay in your kitchen</strong><span>Prompts and files can stay on your device.</span></p>
  <p><strong>Your kitchen stays open</strong><span>Run offline after setup. Keep the model you choose.</span></p>
</div>

<img class="why-sticker" src="assets/tkrobot-original-hands-on-hips.png" alt="T Krobot standing confidently with hands on hips">
<div class="why-caveat">You still pay for hardware, power and upkeep.<br>Cloud features and connected tools can send data out.</div>

<!--
Timing: 35 seconds.

Ordering delivery is convenient, but the bill adds up when you feed people all day. Local inference avoids a provider's per-token bill, which can help with repeated tasks and agents. It is not automatically cheaper: count hardware, electricity and maintenance.

You can keep private ingredients in your kitchen and cook without a connection. Download the model and runtime first. That offline promise covers inference, not web search or other connected tools. You also control which downloaded model version you keep, subject to its licence.

Optional example: Alex Ellis bought four DGX Sparks for his company's private workloads, including testing its own software for vulnerabilities without sending proprietary code to a cloud provider. His reason was control over sensitive data rather than a saving per token. Local models still need supervision and access controls.

[Sources]
- https://lmstudio.ai/docs/app/offline
- https://docs.ollama.com/faq
- https://blog.alexellis.io/how-and-why-we-bought-4-dgx-sparks/ (first-person experience, 15 September 2026)
- Original T Krobot hands-on-hips sticker: https://github.com/tinkertanker/tkrobot-stickers/blob/main/stickers/hands-on-hips.png
-->

---

<!-- _class: why-local-slide why-now-slide -->

# Why local is more practical now

<div class="why-intro">More of the cooking kit is ready to use.</div>

<div class="why-points">
  <p><strong>Cookbooks you can download</strong><span>Open-weight models for chat, coding and more.</span></p>
  <p><strong>Less to set up yourself</strong><span>Apps can download models and serve replies.</span></p>
  <p><strong>More ways to fit the book</strong><span>Quantisation shrinks models. Machines with large unified memory hold more.</span></p>
</div>

<img class="why-sticker" src="assets/tkrobot-original-happy.png" alt="Happy T Krobot with open hands">
<div class="why-caveat">Quality and speed still depend on the model, hardware and task.<br>Sometimes, ordering from the cloud is worth it.</div>

<!--
Timing: 35 seconds.

Local models have been useful for years. What makes them approachable is the combination of downloadable models, easier software and efficient inference on personal hardware. Open-weight means you can obtain the weights under a licence. It does not automatically mean fully open-source or unrestricted use.

Apps can handle downloading and serving. Quantisation reduces the memory required for weights, with possible quality trade-offs. Macs and machines like the DGX Spark share one large pool of memory between the CPU and GPU, so bigger models fit. A model that fits can still be slow, or bad at your task. Next, the cookbook label.

[Sources]
- https://github.com/ggml-org/llama.cpp (model support, quantisation and hardware backends)
- https://lmstudio.ai/docs/app/offline (downloaded models and local serving)
- https://docs.ollama.com/faq (local execution and GPU/CPU placement)
- Original T Krobot happy sticker: https://github.com/tinkertanker/tkrobot-stickers/blob/main/stickers/happy.png
-->

---

<!-- _class: filename-slide -->

# Read the cookbook label

<div class="model-filename"><span>Qwen3.8</span><i>-</i><span>27B</span><i>-</i><span>Q4_K_M</span><span>.gguf</span></div>

<img class="filename-art" src="assets/02-cookbook-label-v2.png" alt="Long-legged T Krobot leaning towards the cookbook label with an open palm against its cover">
<div class="cookbook-cover-label">Qwen3.8-27B<br>Q4_K_M.gguf</div>

<div class="filename-key">
  <p><strong>Qwen3.8</strong><span>Cookbook series and edition</span></p>
  <p><strong>27B</strong><span>Size of the learned recipe knowledge</span></p>
  <p><strong>Q4_K_M</strong><span>More agak-agak, less storage</span></p>
  <p><strong>.gguf</strong><span>Packaging your cooking software can open</span></p>
</div>

<!--
Timing: 45 seconds.

Think of this filename as a cookbook label. Qwen3.8 names the series and edition. 27B is the number of learned parameters: about 28 billion for this model. Bigger models tend to know more, and they need more memory.

Q4_K_M records the measurements with less precision: more agak-agak, less storage. Technically, it is a roughly four-bit mixed K-quantisation preset. GGUF is the file packaging that compatible software can open, including llama.cpp-based tools.

Next we look at the cooking setups that use these books.

[Sources]
- https://huggingface.co/Qwen/Qwen3.8-27B
- https://huggingface.co/bartowski/Qwen3.8-27B-GGUF/blob/main/README.md
- https://github.com/ggml-org/llama.cpp/blob/master/tools/quantize/README.md
- https://github.com/ggml-org/ggml/blob/master/docs/gguf.md
- Cookbook-label illustration regenerated on 12 September 2026 using T Krobot character references.
-->

---

<!-- _class: runtime-tools-slide -->

<img class="runtime-tools-art" src="assets/03-runtime-kitchens-v2.png" alt="One T Krobot reads a recipe in a home kitchen while another runs a busy banquet service">

# Same cookbook.<br>Different setups.

<div class="runtime-tools-list">
  <p><strong>llama.cpp</strong><span>lean C/C++ engine for GGUF models</span></p>
  <p><strong>Ollama</strong><span>downloads, manages and runs models</span></p>
  <p><strong>LM Studio</strong><span>desktop GUI and local server</span></p>
  <p><strong>vLLM</strong><span>high-throughput GPU serving</span></p>
  <p><strong>SGLang</strong><span>programmable high-performance serving</span></p>
</div>


<!--
Timing: 55 seconds.

Now we have read the cookbook label, here are the cooking setups. llama.cpp is a lean C/C++ inference engine that runs GGUF files on CPUs and GPUs. Ollama manages and runs local models. LM Studio adds a desktop interface and local server. vLLM and SGLang focus on efficient serving, especially for many requests. The categories overlap, and the model format still has to match the software.

[Sources]
- https://github.com/ggml-org/llama.cpp
- https://docs.ollama.com/
- https://lmstudio.ai/docs/app/basics/lmstudio-vs-llmster-vs-lms
- https://docs.vllm.ai/en/latest/
- https://docs.sglang.io/
- Cooking-scene artwork generated on 12 September 2026 with character references from https://github.com/tinkertanker/tkrobot-stickers.
-->

---

<!-- _class: image-copy layers-slide -->

<img class="layers-art" src="assets/04-model-cook-manager-v3.png" alt="A cookbook is the model, a T Krobot cook is the runtime, and a second T Krobot managing order tickets is the harness">

# Model, runtime<br>and harness

<div class="layer-list">
  <p><strong>Model: the cookbook</strong><span>Qwen, Gemma, DeepSeek, gpt-oss</span><small>The weights contain what it learned.</small></p>
  <p><strong>Runtime: the cook</strong><span>Any setup from the last slide</span><small>Runs the model to generate replies.</small></p>
  <p><strong>Harness: the manager</strong><span>OpenClaw, OpenCode, Pi</span><small>Manages tools and the agent’s next steps.</small></p>
</div>

<!--
Timing: 55 seconds.

People often use one product name to mean the whole system. In this example, Qwen3.8 is the trained model, Ollama loads and serves it, and OpenClaw owns the conversation, tools and agent loop. Some products cover more than one layer. When something is slow or broken, ask which layer is at fault.

Qwen, Gemma, DeepSeek and gpt-oss are model families. The runtimes are the setups from the previous slide. OpenCode and Pi are coding-agent harnesses. Not every model works with every runtime or harness.

[Sources]
- https://huggingface.co/Qwen/Qwen3.8-27B
- https://docs.ollama.com/
- https://github.com/openclaw/openclaw/blob/main/docs/concepts/agent-loop.md
- https://opencode.ai/docs/
- https://github.com/earendil-works/pi
- https://docs.sglang.io/
- https://ai.google.dev/gemma/docs
- Cooking-scene artwork generated on 12 September 2026 with character references from https://github.com/tinkertanker/tkrobot-stickers.
-->

---

<!-- _class: architecture-slide -->

<img class="architecture-pair" src="assets/05-dense-moe-v2.png" alt="Seated T Krobots consult every section of a dense cookbook or a few selected sections of a thick MoE cookbook, with both whole books present">

# Dense vs MoE

<div class="architecture-subtitle">A token is a small piece of text, often part of a word.</div>

<div class="architecture-grid">
  <div class="architecture-col">
    <h2>DENSE</h2>
    <p>All weights are used for every token.</p>
    <strong>The whole book → each token</strong>
  </div>
  <div class="architecture-col">
    <h2>MIXTURE OF EXPERTS</h2>
    <p>Only selected expert blocks are active for each token.</p>
    <strong>35B total → 3B active</strong>
    <small>Qwen3.6-35B-A3B</small>
  </div>
</div>

<div class="architecture-rule"><strong>Total parameters</strong> shape what must fit. <strong>Active parameters</strong> are a rough guide to work per token.</div>

<!--
Timing: 60 seconds.

A token is a small piece of text, often part of a word. Dense and MoE describe parameter routing. A dense model uses all of its weights for each token. An MoE model keeps all expert weights available, then routes each token through only some expert blocks. Both store the whole cookbook.

Qwen3.6-35B-A3B is the useful filename example: about 35 billion parameters in total and 3 billion activated for a token. You still need memory for all 35 billion. The 3 billion active tells you roughly how much work each token takes, which is why MoE models often run faster than dense models of the same size.

Other labels answer different questions. Transformer, state-space model and hybrid describe the sequence backbone. Text-only and multimodal describe inputs. Base, instruct, reasoning and distilled describe training or behaviour. These labels can stack on one model.

[Sources]
- https://arxiv.org/abs/2211.15841
- https://huggingface.co/Qwen/Qwen3.6-35B-A3B
- https://arxiv.org/abs/2312.00752
- https://www.ai21.com/blog/announcing-jamba/
- Paired cookbook artwork generated on 12 September 2026 with character references from https://github.com/tinkertanker/tkrobot-stickers.
-->

---

<!-- _class: quant-slide -->

# Quantisation

<div class="quant-intro">
  <strong>In a recipe, you can measure precisely, or just agak-agak (roughly).</strong>
  <span>The same learned numbers can be stored using fewer bits.</span>
</div>

<div class="quant-head"><span>FORMAT</span><span>ROUGH WEIGHT STORAGE</span><span>RECIPE VERSION</span></div>
<div class="quant-row"><strong>BF16 / FP16</strong><span>about 2 bytes per parameter</span><span>fine-grained measuring marks</span></div>
<div class="quant-row"><strong>INT8</strong><span>about 1 byte per parameter</span><span>round to the nearest gram</span></div>
<div class="quant-row"><strong>INT4</strong><span>about half a byte, plus scales</span><span>choose one of 16 measuring marks</span></div>
<div class="quant-row"><strong>NVFP4</strong><span>4-bit values, plus scales</span><span>15 uneven marks, rescaled every 16 values</span></div>


<!--
Timing: 50 seconds.

Quantisation stores the model's learned numbers with fewer possible values. It is lossy rounding, not ZIP compression.

The format names tell you how the numbers are represented. BF16 and FP16 use about two bytes per parameter. INT8 uses about one. Four-bit formats use about half a byte per parameter before scales and other metadata. INT4 gives each number one of 16 evenly spaced marks.

NVFP4 is NVIDIA's 4-bit floating-point format. Four bits give 16 patterns, but plus zero and minus zero are the same, so there are 15 usable values: 0, 0.5, 1, 1.5, 2, 3, 4 and 6, positive or negative. The marks are closer together near zero, where most weights sit. Every block of 16 values shares its own scale factor, so each block's marks are stretched to fit that block's range, and one more scale covers the whole tensor. It is like a measuring jug with uneven markings that you swap for a bigger or smaller jug every 16 ingredients. MXFP4 is another block-scaled 4-bit format used for most of the MoE weights in gpt-oss. Quality and speed vary with the model, runtime and task.

[Sources]
- https://docs.nvidia.com/deeplearning/tensorrt/latest/inference-library/data-format-desc.html
- https://docs.nvidia.com/deeplearning/transformer-engine/user-guide/features/low_precision_training/nvfp4/nvfp4.html
- https://cdn.openai.com/pdf/419b6906-9da6-406c-a19d-1bb078ac7637/oai_gpt-oss_model_card.pdf
-->

---

<!-- _class: image-copy memory-slide -->

<img class="memory-art" src="assets/06-memory-counter.png" alt="T Krobot at a crowded kitchen counter with order slips moving along a conveyor">

# Fit is one thing.<br>Speed is another.

<div class="plain-copy definitions">
  <p><strong>Memory capacity</strong><br>How much can fit at once</p>
  <p><strong>Memory bandwidth</strong><br>How quickly weights can be read</p>
</div>

<div class="term-line">Capacity is VRAM on a GPU, or unified memory on Macs and DGX Spark. Bandwidth is measured in GB/s.</div>

<!--
Timing: 40 seconds.

Capacity and bandwidth answer different questions. Memory capacity is the size of the counter: VRAM on a graphics card, or unified memory shared by the CPU and GPU on Macs and the DGX Spark. The model weights, the current context and temporary working memory must share it.

Memory bandwidth is how quickly the hardware can read those weights while generating. A machine can have enough capacity for a large model and still generate slowly. Another machine can be fast but too small for the model you want.

[Sources]
- https://developer.nvidia.com/blog/mastering-llm-techniques-inference-optimization/
- Illustration generated for this deck using the T Krobot illustration skill from https://github.com/tinkertanker/tkrobot-stickers on 27 August 2026.
-->

---

<!-- _class: memory-headroom-slide -->

<img class="headroom-art" src="assets/11-short-long-context.png" alt="T Krobot comparing a short chat with a long chat that uses more counter space">

# The model fits.<br>The conversation might not.

<div class="headroom-labels">
  <p><strong>Short chat</strong><span>Room for context and working memory</span></p>
  <p><strong>Long chat</strong><span>Same weights, larger KV cache</span></p>
</div>

<div class="headroom-defs">
  <p><strong>Context</strong>The text the model can currently attend to</p>
  <p><strong>KV cache</strong>Saved keys and values from earlier tokens</p>
</div>

<!--
Timing: 50 seconds.

Context is the instructions, conversation and generated text that the model can currently attend to.

While processing that text, the model computes keys and values for every token. The KV cache keeps them so the model does not recompute them for earlier tokens each time it generates a new one.

The weights stay the same size, but the KV cache grows with the conversation. So a model that fits with a short prompt can run out of memory in a long chat, or with many people using it at once. How fast it grows depends on the model's design, the context length and the cache settings.

Prefix caching reuses KV data when a later request starts with exactly the same text, if the runtime supports it and the cache is still there. Think of keeping the same prepared ingredients ready for the next order. It saves prompt processing, not reply generation. A cold prompt has nothing reusable cached. That's separate from whether the model itself is already loaded.

[Sources]
- https://huggingface.co/docs/transformers/main/en/kv_cache
- https://docs.vllm.ai/en/latest/features/automatic_prefix_caching/
- Illustration generated for this deck using the T Krobot illustration skill from https://github.com/tinkertanker/tkrobot-stickers on 5 September 2026.
-->

---

<!-- _class: fit-slide fit-combined -->

# What fits in local memory?

<div class="fit-rule"><span>These examples may fit in memory, but that does not tell you how fast they run.</span></div>

<div class="fit-table">
  <div class="fit-row fit-header"><span>Memory target</span><span>Model</span><span>What the size means</span></div>
  <div class="fit-row"><strong>8 GB</strong><span>Gemma 4 E4B</span><span>Q4_0 load ≈ 4.5 GB</span></div>
  <div class="fit-row"><strong>16 GB</strong><span>Gemma 4 12B</span><span>Q4_0 load ≈ 6.7 GB</span></div>
  <div class="fit-row"><strong>16 GB</strong><span>gpt-oss-20b</span><span>OpenAI: runs in 16 GB with MXFP4</span></div>
  <div class="fit-row"><strong>24 GB</strong><span>Qwen3.8-27B</span><span>Q4_K_M file 17.8 GB</span></div>
  <div class="fit-row"><strong>24 GB</strong><span>Gemma 4 31B</span><span>Q4_0 load ≈ 17.5 GB</span></div>
  <div class="fit-row"><strong>80 GB</strong><span>gpt-oss-120b</span><span>OpenAI: one 80 GB GPU, MXFP4</span></div>
  <div class="fit-row"><strong>128 GB*</strong><span>GLM-5.3-Flash</span><span>UD-IQ1_S file 93.1 GB; aggressive quant</span></div>
  <div class="fit-row"><strong>256 GB*</strong><span>GLM-5.3</span><span>UD-IQ2_M file 239 GB; aggressive quant</span></div>
</div>

<div class="fit-footer">The model shares memory with its context and software, including the OS on unified-memory systems.<br><small>*We have not tested the 128/256 GB setups. Their low-bit quantisation may reduce quality.</small></div>

<!--
Timing: 60 seconds.

These are rough targets. The gpt-oss rows come straight from OpenAI. The Gemma figures are Google's Q4_0 loading estimates, which include a loading allowance but not context or other software. Qwen's 17.8 GB is the file size, not measured memory use.

The GLM rows are community low-bit builds from Unsloth, and we haven't tried them. GLM-5.3-Flash has 320 billion parameters with 18 billion active; its 1-bit build is a 93 GB file and Unsloth suggests about 102 GB of memory. The full GLM-5.3 build is 239 GB, and Unsloth asks for at least 245 GB. Squeezing a model this hard costs quality. DeepSeek-V4.1-Flash is bigger again, about 750 billion parameters, so even its 1-bit build is around 250 GB.

Leave headroom for context and, on unified memory, the operating system. Sources checked 11 November 2026. Pick a few rows to talk through rather than reading them all.

[Sources]
- https://ai.google.dev/gemma/docs/core
- https://ai.google.dev/gemma/docs/core/model_card_4
- https://huggingface.co/Qwen/Qwen3.8-27B
- https://huggingface.co/bartowski/Qwen3.8-27B-GGUF/blob/main/README.md
- https://openai.com/index/introducing-gpt-oss/
- https://unsloth.ai/docs/models/glm-5.3-flash
- https://huggingface.co/unsloth/GLM-5.3-Flash-GGUF
- https://unsloth.ai/docs/models/glm-5.3
- https://huggingface.co/unsloth/GLM-5.3-GGUF
- https://unsloth.ai/docs/models/deepseek-v4.1-flash
- https://huggingface.co/docs/transformers/main/en/kv_cache
-->

---

<!-- _class: image-copy speed-slide -->

![bg](assets/09-serving-speed-v2.png)

<img class="speed-sticker speed-waiting" src="assets/tkrobot-original-waiting.png" alt="Original T Krobot open-palm waiting pose">
<img class="speed-sticker speed-running" src="assets/tkrobot-original-running.png" alt="Original T Krobot running pose">

# TTFT and TPS

<div class="speed-defs">
  <p><strong>TTFT</strong><span>Time to first token</span><small><b>Prefill:</b> process the prompt before answering</small></p>
  <p><strong>TPS</strong><span>Tokens per second after that</span><small><b>Decode:</b> generate the reply one token at a time</small></p>
</div>

<!--
Timing: 40 seconds.

Two systems can both feel slow, for different reasons. TTFT means time to first token: how long you wait before anything appears. Prefill is the phase where the model processes the prompt before producing that first output token.

TPS means tokens per second after generation has started. Decode is the phase where the model generates the answer one token at a time.

In a chat you feel both. Fast streaming won't make up for a long wait at the start.

[Sources]
- https://docs.vllm.ai/en/latest/features/per_request_metrics/
- https://docs.vllm.ai/en/latest/usage/metrics/
- Serving-hatch artwork generated on 12 September 2026. Original palm-open and running-right stickers from https://github.com/tinkertanker/tkrobot-stickers/tree/f4e93c2ba5c8c955e39c564491f6c4b22b7d1f7d/stickers, used unchanged.
-->

---

<!-- _class: benchmark-slide -->

# Speed claims need a recipe

<div class="benchmark-intro">How many orders, what dish, and how much prep?</div>
<div class="benchmark-terms">
  <p><strong>C1 / C4: concurrency</strong><span>One / four requests in flight. One agent can launch several.</span></p>
  <p><strong>Cold prompt / prefix cache hit</strong><span>Prep from scratch, or reuse matching earlier work.</span></p>
  <p><strong>Per-user speed / total throughput</strong><span>Your plates per minute, or the whole kitchen’s output?</span></p>
  <p><strong>Speculative decoding / acceptance rate</strong><span>A drafter suggests tokens. The main model checks them.<br>How many suggestions survive?</span></p>
</div>
<img class="benchmark-sticker" src="assets/tkrobot-original-sus.png" alt="T Krobot looking sceptically at a performance claim">
<div class="benchmark-takeaway">A useful benchmark shows how long you wait and how fast the reply arrives,<br>using the same task and settings.</div>

<!--
Timing: 55 seconds.

C1 and C4 mean one and four requests running at once. That's requests, not people: one agent with four subagents is already C4 or more. More simultaneous requests can increase total server output while slowing each user's stream. Report both, and include time waiting in the queue when measuring the user's experience.

Cold versus cached here refers to the prompt prefix. Keep model load state separate. Fix input and output lengths, reasoning settings, model/quantisation, hardware and runtime when comparing runs.

Speculative decoding uses a cheaper proposal method, such as a smaller draft model, then verifies proposed tokens with the target model. Acceptance rate is the fraction of proposed tokens accepted. High acceptance helps, but drafting and checking take time too, so it can still end up slower. MTP, multi-token prediction, is built into some models and often acts as the drafter. What's supported depends on the model and runtime.

Alex Ellis runs GLM-5.3-Flash across his four DGX Sparks, and his own measurements show how much the task matters. On the same setup he got about 30 tokens per second writing prose, 75 writing code and 110 for structured output. Structured output is predictable, so more of the drafter's guesses survive. A cold 64,000-token prompt took about 28 seconds to process; replayed from the prefix cache, under two. On his real agent traffic, about 45 is typical. Earlier, a two-Spark recipe advertised 65 to 85 tokens per second, which turned out to be measured on a counting task; he saw 30 to 40 in normal use. So test with your own work before trusting a headline number.

[Sources]
- https://blog.alexellis.io/how-and-why-we-bought-4-dgx-sparks/ (two-Spark recipe example)
- https://github.com/alexellis/glm-5.3-flash-4x-dgx-spark-switchless (measurements from 5 September 2026)
- https://docs.vllm.ai/en/latest/cli/bench/serve/ (concurrency and controlled benchmark inputs)
- https://docs.vllm.ai/en/latest/features/automatic_prefix_caching/
- https://docs.vllm.ai/en/latest/features/speculative_decoding/
- Original sticker: https://github.com/tinkertanker/tkrobot-stickers/blob/main/stickers/sus.png
-->

---

<!-- _class: tp-slide -->

![bg](assets/10-shared-recipe-v2.png)

# One model across several GPUs

<div class="tp-defs">
  <p><strong>TP</strong><span>Split each layer's maths across GPUs</span></p>
  <p><strong>Within one machine</strong><span>NVLink or PCIe</span></p>
  <p class="tp-between"><img src="assets/04-tp-roce-inset.png" alt="A dumbwaiter carrying dishes between two kitchens over a RoCE rope"><strong>Between machines</strong><span>RoCE or InfiniBand</span></p>
</div>

<div class="tp-nccl"><strong>NCCL</strong>: software that coordinates GPU communication</div>

<!--
Timing: 55 seconds.

Tensor parallelism splits one model's tensor operations and weights across several GPUs. Each GPU does part of the work, then exchanges partial results with the others again and again.

A node is one machine. Inside one, GPUs talk over NVLink where the system has it, otherwise over PCIe. RoCE means RDMA over Converged Ethernet, and InfiniBand is another fast network fabric used between machines.

Pooling memory is only half of it. The GPUs talk to each other constantly, so the link between them matters. Alex Ellis's four Sparks run one model at TP4, linked in a ring over RoCE with no network switch.

NCCL, pronounced nickel, is NVIDIA's Collective Communications Library. It supplies operations that exchange and combine data among GPUs, within or across machines. In the kitchen analogy, it organises the hand-offs between cooks. The network fabric is the connection those hand-offs travel over. TP4 means four tensor-parallel participants, not four independent model copies. Linking machines does not automatically turn their RAM into one transparent pool.

[Sources]
- https://docs.vllm.ai/en/latest/serving/parallelism_scaling/
- https://github.com/alexellis/glm-5.3-flash-4x-dgx-spark-switchless
- https://docs.nvidia.com/deeplearning/nccl/user-guide/docs/overview.html
- https://docs.nvidia.com/networking-ethernet-software/cumulus-linux/Layer-1-and-Switch-Ports/Quality-of-Service/RDMA-over-Converged-Ethernet-RoCE/
- Shared-recipe and RoCE dumbwaiter artwork generated with character references from https://github.com/tinkertanker/tkrobot-stickers.
-->

---

<!-- _class: end-slide -->
<!-- _paginate: false -->

![bg](assets/13-finished-meal-v2.png)

<img class="end-sticker" src="assets/tkrobot-original-tummy.png" alt="Original T Krobot rubbing its tummy after a meal">
<img class="end-table-front" src="assets/13-finished-meal-v2.png" alt="">

# Fits. Fast.<br>Worth it?

<div class="end-summary">
  <p><strong>Fits?</strong><span>Weights, context and working memory</span></p>
  <p><strong>Fast?</strong><span>Bandwidth, compute, TTFT and TPS</span></p>
  <p><strong>Worth it?</strong><span>Privacy and control versus effort and trade-offs</span></p>
</div>

<!--
Timing: 20 seconds.

Local AI comes down to three questions: does the whole cookbook fit on the counter, do the plates arrive fast enough, and is running your own kitchen worth it? Now, when someone says “27B Q4 GGUF”, you know what to ask next.

[Sources]
- Table artwork generated on 12 September 2026. Original rubbing-tummy sticker from https://github.com/tinkertanker/tkrobot-stickers/tree/f4e93c2ba5c8c955e39c564491f6c4b22b7d1f7d/stickers, used unchanged.
-->
