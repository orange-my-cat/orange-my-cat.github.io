---
title: "Localizing LLaMas"
date: 2023-04-20
tags: ["knowledge", "machine_learning"]
---

A [llama](https://en.wikipedia.org/wiki/Llama) is a South American relative of camels, though without the humps. A [LLaMa](https://ai.facebook.com/blog/large-language-model-llama-meta-ai/) however, is a foundational large langauge model released by Meta.

![llama.png](/blogs/llama.png)

AI tools like ChatGPT and Bard has been gaining popularity lately, and as a science student, of course I would want to learn about their behind the scenes tech stuff. Although LLaMa may seem similar to ChatGPT and Bard, it is in fact quite different. While ChatGPT and Bard is an entire usable application, LLaMa is just the brains behind AI applications. Therefore, the topic that we're going to look into today is not AI tools, but rather the language models behind the tools. 

There exists only a handful of large language models as compared to AI tools today, with everyone coming up with their own versions. Though the models behind the tools are all quite similar, with more notable ones would be GPT-3/GPT-4 used in ChatGPT and LaMDA used in Bard. As LLaMa is open sourced, I decided to look into it as a way for me to explore the world of large language models.

To run LLaMa on your local machine, just clone the LLaMa [repository](https://github.com/facebookresearch/llama), and download the weights. After that, it's all quite straightforward as documented in their readme file.

For my setup, I just used my laptop with a AMD Ryzen 7 6800HS (not much but yea). As my GPU is unable to support CUDA (AMD GPU), I changed edited parts of the code to let the model only run on my CPU. Performance wise, it wasn't good, but I wouldn't say that it's bad either. Loading up the 7B model took around 45 seconds on average, and inferences took about 1 second for each word generated. I should also mention that it took up more than 24GB of my RAM to run the model.

It is important to understand that the weights for the LLaMa model provided in the repository works by taking a sequence of words as an input and predicts a next word to recursively generate text. I modified it to become a chat bot by implementing a simple workaround. By changing the input prompt to *"The expected response for a highly intelligent chatbot to __prompt__ is:"*, I successfully turned it's responses into conversational type responses.

To further tune the model, we can change up parameters like temperature, top_p, max_seq_len, max_batch_size, and max_gen_len. These parameters correspond to:

- __temperature__: A parameter that controls the randomness of the generated text.
- __top_p__: A parameter that controls the nucleus sampling strategy, which is a method that selects only the most probable tokens.
- __max_seq_len__: The maximum sequence length for the input and output of the model. 
- __max_batch_size__: The maximum number of input sequences that the model can process in parallel.
- __max_gen_len__: The maximum number of words that the model will generate as a response.

![llama_prompts.png](/blogs/llama_prompts.png)