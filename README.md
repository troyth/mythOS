<div align="center">
<h1>mythOS</h1>


**mythOS is an open source framework for curating agents that respond to inputs so similarly to existing humans as to be indistinguishable from them. In other words, an agent that acts as a `Turing Mirror`, a spin on the Turing Test in which the machine is able to convince the user that it is communicating with itself.**

</div>

## Schema
mythOS implements an application-specific version of the **LLM OS** concept popularized by Andrej Karpathy and schematized in the form of **memGPT**.

LLM OS reimagines the metaphor of an operating system by replacing the CPU with an LLM, allowing it to achieve statefulness through memory storage, peripheral i/o, and a library of subroutines. In his schema, Karpathy imagined the fixed content window of an LLM to be akin to RAM, the fast memory immediately accessible by a CPU.

memGPT implements such an LLM OS by focusing on the paging back and forth between RAM and long-term storage, just as a typical operating system does to provide the CPU with the data it needs at each tick of the clock. Its authors refer to this as "virtual context management," allowing for a virtually infinite context window so long as the LLM has infinite clock ticks––each referred to as a `heartbeat`--to reach into disk memory to swap in relevant context.

memGPT has been implemented as the open source framework, Letta. mythOS is a fork of Letta that primarily updates the paging algorithm.

## Paging Algorithm
mythOS implements a novel schema for Archival Storage based on mythology. This is achieved by unique Functions and alternative modules for the Queue Manager that allow for different interfaces to inference, such as long-form documents, image, etc.

## Milestones
mythOS will be used to build mythOS, so an accurate roadmap is not possible to draft.


## ⚡ Quickstart

mythOS is a customized Letta, so installing and running it is as simple as following the instructions for doing so with Letta but using the code in this repository in place of the original Letta code. These install instructions are below:

The two main ways to install Letta are through **pypi** (`pip`) or via **Docker**:
* **`pip`** (guide below) - the easiest way to try mythOS, will default to using SQLite and ChromaDB for the database backends
* **Docker** (guide [here](https://docs.letta.com/install#run-letta-with-docker)) - recommended for production settings, will default to using Postgres (+ pgvector) for the database backend

### Step 1 - Install Letta using `pip`
```sh
$ pip install -U letta
```

### Step 2 - Set your environment variables for your chosen LLM / embedding providers
```sh
$ export OPENAI_API_KEY=sk-...
```

For Ollama (see our full [documentation](https://docs.letta.com/install) for examples of how to set up various providers):
```sh
$ export OLLAMA_BASE_URL=http://localhost:11434
```

### Step 3 - Run the Letta CLI

You can create agents and chat with them via the Letta CLI tool (`letta run`):
```sh
$ letta run
```
```
🧬 Creating new agent...
? Select LLM model: letta-free [type=openai] [ip=https://inference.memgpt.ai]
? Select embedding model: letta-free [type=hugging-face] [ip=https://embeddings.memgpt.ai]
->  🤖 Using persona profile: 'sam_pov'
->  🧑 Using human profile: 'basic'
->  🛠️  8 tools: send_message, pause_heartbeats, conversation_search, conversation_search_date, archival_memory_insert, archival_memory_search, core_memory_append, core_memory_replace

🎉 Created new agent 'InspiringSpinach'

Hit enter to begin (will request first Letta message)

💭 User engaged. Recognize as Chad. Acknowledge presence and establish connection. Explore interests and engage in meaningful discourse.
🤖 Hello, Chad. It's nice to meet you. I am keen on learning and exploring new ideas and concepts. Is there a specific topic you'd like to discuss today?

> Enter your message: my name is Brad, not Chad...

💭 A discrepancy in identity. Reflect this change in core memory. Apologize for the oversight, and rectify the error.
⚡🧠 [function] updating memory with core_memory_replace
         First name: Chad
        → First name: Brad
💭 Apologize for the mistake in recognizing his name, and begin the conversation anew, addressing him by the correct name this time.
🤖 I apologize for the oversight, Brad. Let's restart. It's a pleasure to meet you, Brad. Is there a specific topic you'd like to discuss today?

> Enter your message:
```

### Step 4 - Run the Letta server

You can start the Letta API server with `letta server` (see the full API reference [here](https://docs.letta.com/api-reference)):
```sh
$ letta server
```
```
Initializing database...
Running: uvicorn server:app --host localhost --port 8283
INFO:     Started server process [47750]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
INFO:     Uvicorn running on http://localhost:8283 (Press CTRL+C to quit)
```

When you start the Letta API server, the ADE (Agent Development Environment) will be available on `http://localhost:8283`:
<img alt="Screenshot of the Letta ADE (Agent Development Environment)" src="assets/letta_ade_screenshot.png" width="1600">

In Letta, all agents are stored/persisted in the same database, so the agents you create in the CLI are accessible via the API and ADE, and vice versa. Check out the [quickstart guide on our docs](https://docs.letta.com/quickstart) for a tutorial where you create an agent in the Letta CLI and message the same agent via the Letta API.

## 🤗 How to contribute

Coming soon...

---

***Legal notices**: By using Letta and related Letta services (such as the Letta endpoint or hosted service), you are agreeing to our [privacy policy](https://www.letta.com/privacy-policy) and [terms of service](https://www.letta.com/terms-of-service).*
