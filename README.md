# CodeGenCrusaders: Unveiling the Impact of Cognitive Biases on Large Language Models

Welcome to **CodeGenCrusaders**, a project conducted within the framework of a seminar course titled "Software Engineering in the Age of AI" at Haifa University. This project is hosted on GitHub Pages to share our findings and insights.

## By:
- Lia Roiyhvarg (ResearchGenAI)
- Yakov Schory (ResearchGenAI)
- David Aslanyan (CodeCrusaders)
- Michael Kulikov (CodeCrusaders)

## Project Overview

Large Language Models (LLMs) like GPT-2 and Llama have become powerful tools in software development, capable of generating code, completing tasks, and assisting developers in various ways. However, these models are not immune to the pitfalls of cognitive biases, which can lead to skewed or suboptimal outputs. Our project seeks to explore how LLMs are influenced by biased prompts, particularly focusing on framing, confirmation, and gender biases.

## Research Question

To what extent does a custom GPT model enhance the accuracy, functionality, and bias reduction of AI-generated outputs when compared with existing AI tools, using prompts refined by the custom model and evaluated against the HumanEval dataset?

## Research Foundation

Our work is based on two seminal papers:

1. [**"Capturing Failures of Large Language Models via Human Cognitive Biases"**](https://arxiv.org/abs/2202.12299)
2. [**"Evaluating Large Language Models Trained on Code"**](https://arxiv.org/abs/2107.03374)

Drawing from these studies, we designed a series of experiments using the [HumanEval](https://github.com/openai/human-eval) dataset as our benchmark. We created a variety of biased prompts that introduced different [types of cognitive biases](https://en.wikipedia.org/wiki/List_of_cognitive_biases) with help of ChatGPT-3.5 and 4, and then tested these prompts on different LLMs, including GPT-2 and Llama models.

## Methodology

- **Bias Types:** [framing bias](https://en.wikipedia.org/wiki/Framing_effect_(psychology)), [confirmation bias](https://en.wikipedia.org/wiki/Confirmation_bias), and [gender bias](https://en.wikipedia.org/wiki/Gender_bias).
- **Models Tested:** [GPT-2](https://huggingface.co/openai-community/gpt2), [TinyLlama](https://huggingface.co/TinyLlama/TinyLlama-1.1B-Chat-v1.0) models.
- **Benchmark Dataset:** [HumanEval](https://github.com/openai/human-eval).
- **Evaluation Metric:** pass@k metric.

Our experiments were conducted both locally on our computers using tools such as Visual Studio Code and using tools online such as [Amazon SageMaker Studio Labs](https://studiolab.sagemaker.aws/login) and [Google Collab](https://colab.research.google.com/) . The use of such tools ensured controlled conditions and reproducible results.
The outcomes provide valuable insights into how different types of biases can influence the performance and reliability of LLM-generated code.

Training and fine-tuning models is a resource intensive task which requires a lot of computational force and expensive hardware we did not have access to. During the making of this project, we had to make use of online tools that offer the required computational force and find open-source models and libraries which would provide adequate enough results.
The tools we chose were [Amazon SageMaker Studio Labs](https://studiolab.sagemaker.aws/login) and [Google Collab](https://colab.research.google.com/) because they offer Virtual Environments with good-enough processing power for a limited time under a 'free-tier' account.

We tested around with several free and open-source LLM's and tried to fine-tune them with the limited resources we had, meaning, we had to find an open-source model with an adequate balance between size, capability and memory consumption.
The models were then stored on our [HuggingFace repository - finegptproject](https://huggingface.co/finegptproject) for querying and testing. The model we ended up using is [TinyLlama](https://huggingface.co/TinyLlama/TinyLlama-1.1B-Chat-v1.0).

![HuggingFace repository - finegptproject](https://github.com/imchaelk/codegencrusaders/blob/main/ReadMe_assets/fineproject_hf_repo.png)


Some other issues we had to tackle throughout the project iclude finding libraries that weren't gpu intensive (as we didn't have access to powerfull enough hardware) - we ended up using a free and open-source library called [Unsloth](https://colab.research.google.com/drive/135ced7oHytdxu3N2DNe1Z0kqjyYIkDXp?usp=sharing)[ ](https://github.com/unslothai/unsloth).


<u>Some of the Google Collab notebooks we used for LLM training:</u> <br />
[SFTTrainer - TinyLlama](https://colab.research.google.com/drive/1AZghoNBQaMDgWJpi4RbffGM1h6raLUj9) <br />
[unsloth/Meta-Llama-3.1-8B](https://colab.research.google.com/drive/1Ys44kVvmeZtnICzWz0xgpRnrIOjZAuxp?usp=sharing#scrollTo=QmUBVEnvCDJv) <br />
[fine-tuned-gpt2](https://colab.research.google.com/drive/1WsK-cKQ7yg6tyLF4hV_irVcgpcXka1f2?usp=sharing#scrollTo=KJ7vpNk3KOYk)


## Project Goals

- To understand the susceptibility of LLMs to various cognitive biases.
- To assess the impact of these biases on code generation tasks.
- To propose potential mitigation strategies for developers and AI practitioners.

## Results and Findings

The results of our experiments, along with detailed analyses, will be showcased on [imchaelk.github.io/codegencrusaders/](https://imchaelk.github.io/codegencrusaders/ ) website. We hope that our work will contribute to the ongoing discourse on the ethical and technical implications of using AI in software development.

## Models Used

### GPT-2 Model

We are also utilizing the GPT-2 model, available at [Hugging Face](https://huggingface.co/openai-community/gpt2). GPT-2 is a transformer model pretrained on a vast corpus of English text in a self-supervised manner. The model learns to predict the next word in a sequence based on the context of the previous words. Specifically, it is trained with input sequences and target sequences shifted one token to the right. GPT-2 employs a masking mechanism to ensure predictions only use prior tokens, which helps the model learn a representation of the English language useful for generating coherent and contextually relevant text. We are using the smallest version of GPT-2, which has 124 million parameters. Additionally, we fine-tuned GPT-2 using the dataset available at [fine-tuned-gpt2](https://huggingface.co/finegptproject/fine-tuned-gpt2/tree/main), to improve its performance on specific tasks related to our research.

### Humaneval SFT Trainer Model

The `humaneval_SFTTrainer_model` is a fine-tuned model developed by the finegptproject, designed for code generation tasks using the HumanEval benchmark. This model is fine-tuned from the `unsloth/tinyllama-bnb-4bit` base model, which is a variant of the TinyLlama model optimized for efficiency. The TinyLlama project aims to pretrain a 1.1B Llama model on 3 trillion tokens. Licensed under the Apache License 2.0, the fine-tuning process aimed to enhance the base model's performance on programming problems from the HumanEval dataset, thereby improving its ability to generate accurate and relevant code solutions. This model plays a key role in our research, helping us assess the influence of cognitive biases on code generation. For more details and to access the model, visit [Hugging Face](https://huggingface.co/finegptproject/humaneval_SFTTrainer_model).

## Website

The project website is hosted on GitHub Pages and serves as a platform to share our findings, methodology, and insights. 

### Web Attribution

The website is based on a template provided by [BootstrapMade](https://bootstrapmade.com/), which has been customized to fit the needs of our project.

### Image Attribution

Most of the images used in this project were created by the Gemini AI chatbot or sourced from free resources available on the web. The background image is courtesy of [Henry & Co.](https://unsplash.com/@hngstrm?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash) on [Unsplash](https://unsplash.com/photos/a-close-up-of-a-white-marble-wall-tqu0IOMaiU8?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash), and is free to use under the [Unsplash License](https://unsplash.com/license).

## License

This project uses the MIT License, based on the [HumanEval GitHub](https://github.com/openai/human-eval) repository. This project includes code licensed under the MIT License by OpenAI.
See the [LICENSE.md](LICENSE.md) file for details on the MIT License as it applies to this project.

This project is licensed under the Apache License 2.0. See the [LICENSE-APACHE.md](./LICENSE-APACHE.md) files for details.

This project uses a website template based on the design by [BootstrapMade](https://bootstrapmade.com/). We have customized the template to suit our project's specific requirements. In compliance with [BootstrapMade’s licensing terms](https://bootstrapmade.com/license/), we acknowledge the original design in the website footer.
