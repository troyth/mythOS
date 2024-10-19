# AION

AION, or **An I Object Notation**, is implemente by `.aion` files that provide rich configuration information sufficient to specify an LLM to act as a CPU in an LLM OS implementation.

MYTH.OS uses Ollama to serve local models. Each time MYTH.OS loads a core LLM, it spawns an instance of the model specified by the `.aion` file of the core LLM and uses the other properties to package any prompts sent to it, such as control vectors and fine-tuning parameters.

## Required Properties
* `id` (string) : a unique identifier (MYTH.OS uses the created at timestamp hashed with the initial system prompt)
* `model` (string) : the name of the LLM model using Ollama syntax
* `systemPrompt` (string) : the system prompt for the model

## Optional Properties
* `humanPrompt` (string) : the human prompt for the model
* `tools` (array of objects)
* `databases` (array of objects)
