# UdditdocGPT 
![Apr 22, 2025, 03_36_46 PM](https://github.com/user-attachments/assets/2a9d38ad-7d35-4211-841b-160da5622f5e)

[![Website](https://img.shields.io/website?up_message=check%20it&down_message=down&url=https%3A%2F%2Fudditwork.github.io%2FPORTFOLIO-Uddit%2F&label=Portfolio)](https://udditwork.github.io/PORTFOLIO-Uddit/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin)](https://linkedin.com/in/lorduddit-/)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?logo=github)](https://github.com/UDDITwork)
[![YouTube](https://img.shields.io/badge/YouTube-Subscribe-red?logo=youtube)](https://www.youtube.com/@uddit748)
[![ResearchGate](https://img.shields.io/badge/ResearchGate-Follow-green?logo=researchgate)](https://www.researchgate.net/profile/Uddit)

![UdditdocGPT UI](/assets/ui.png?raw=true)

UdditdocGPT is a production-ready AI project that allows you to ask questions about your documents using the power
of Large Language Models (LLMs), even in scenarios without an Internet connection. 100% private, no data leaves your
execution environment at any point.

>[!TIP]
> If you are looking for an **enterprise-ready, fully private AI workspace**
> check out my [Portfolio](https://udditwork.github.io/PORTFOLIO-Uddit/) or [contact me](mailto:udditkantsinha2@gmail.com) for a demo.
> Crafted by Uddit Kant Sinha, UdditdocGPT is a best-in-class AI document analyzer that can be easily deployed on-premise (data center, bare metal...) or in your private cloud (AWS, GCP, Azure...).

The project provides an API offering all the primitives required to build private, context-aware AI applications.
It follows and extends the [OpenAI API standard](https://openai.com/blog/openai-api),
and supports both normal and streaming responses.

The API is divided into two logical blocks:

**High-level API**, which abstracts all the complexity of a RAG (Retrieval Augmented Generation)
pipeline implementation:
- Ingestion of documents: internally managing document parsing,
splitting, metadata extraction, embedding generation and storage.
- Chat & Completions using context from ingested documents:
abstracting the retrieval of context, the prompt engineering and the response generation.

**Low-level API**, which allows advanced users to implement their own complex pipelines:
- Embeddings generation: based on a piece of text.
- Contextual chunks retrieval: given a query, returns the most relevant chunks of text from the ingested documents.

In addition to this, a working [Gradio UI](https://www.gradio.app/)
client is provided to test the API, together with a set of useful tools such as bulk model
download script, ingestion script, documents folder watch, etc.

## 🎞️ Overview
>[!WARNING]
>  This README is not updated as frequently as the documentation.
>  Please check the docs for the latest updates!

### Motivation behind UdditdocGPT
Generative AI is a game changer for our society, but adoption in companies of all sizes and data-sensitive
domains like healthcare or legal is limited by a clear concern: **privacy**.
Not being able to ensure that your data is fully under your control when using third-party AI tools
is a risk those industries cannot take.

As a PatentTech innovator and AI Engineer, I created UdditdocGPT to address these concerns head-on.

### Evolution of UdditdocGPT
UdditdocGPT is evolving towards becoming a gateway to generative AI models and primitives, including
completions, document ingestion, RAG pipelines and other low-level building blocks.
I want to make it easier for any developer to build AI applications and experiences, as well as provide
a suitable extensive architecture for the community to keep contributing.

Stay tuned to the [releases](https://github.com/UDDITwork/UdditdocGPT/releases) to check out all the new features and changes included.

## 📄 Documentation
Full documentation on installation, dependencies, configuration, running the server, deployment options,
ingesting local documents, API details and UI features can be found in the project documentation.

## 🧩 Architecture
Conceptually, UdditdocGPT is an API that wraps a RAG pipeline and exposes its
primitives.
* The API is built using [FastAPI](https://fastapi.tiangolo.com/) and follows
  [OpenAI's API scheme](https://platform.openai.com/docs/api-reference).
* The RAG pipeline is based on [LlamaIndex](https://www.llamaindex.ai/).

The design of UdditdocGPT allows to easily extend and adapt both the API and the
RAG implementation. Some key architectural decisions are:
* Dependency Injection, decoupling the different components and layers.
* Usage of LlamaIndex abstractions such as `LLM`, `BaseEmbedding` or `VectorStore`,
  making it immediate to change the actual implementations of those abstractions.
* Simplicity, adding as few layers and new abstractions as possible.
* Ready to use, providing a full implementation of the API and RAG
  pipeline.

Main building blocks:
* APIs are defined in `udditdoc_gpt:server:<api>`. Each package contains an
  `<api>_router.py` (FastAPI layer) and an `<api>_service.py` (the
  service implementation). Each *Service* uses LlamaIndex base abstractions instead
  of specific implementations,
  decoupling the actual implementation from its usage.
* Components are placed in
  `udditdoc_gpt:components:<component>`. Each *Component* is in charge of providing
  actual implementations to the base abstractions used in the Services - for example
  `LLMComponent` is in charge of providing an actual implementation of an `LLM`
  (for example `LlamaCPP` or `OpenAI`).

## 💡 Contributing
Contributions are welcomed! To ensure code quality I have enabled several format and
typing checks, just run `make check` before committing to make sure your code is ok.
Remember to test your code! You'll find a tests folder with helpers, and you can run
tests using `make test` command.

Don't know what to contribute? Check out the 
[Project Board](https://github.com/UDDITwork/UdditdocGPT/projects) with several ideas.

Head over to our communication channels and ask for write permissions on the GitHub project.

## 💬 Community
Join the conversation around UdditdocGPT on:
- [LinkedIn](https://linkedin.com/in/lorduddit-/)
- [GitHub](https://github.com/UDDITwork)
- [YouTube](https://www.youtube.com/@uddit748)

## 📖 Citation
If you use UdditdocGPT in a paper, please cite it appropriately.

Here are a couple of examples:

#### BibTeX
```bibtex
@software{Uddit_UdditdocGPT_2025,
author = {Uddit Kant Sinha},
license = {Apache-2.0},
month = april,
title = {{UdditdocGPT}},
url = {https://github.com/UDDITwork/UdditdocGPT},
year = {2025}
}
```

#### APA
```
Uddit Kant Sinha (2025). UdditdocGPT [Computer software]. https://github.com/UDDITwork/UdditdocGPT
```

## 📑 Related Projects
UdditdocGPT complements my other AI initiatives:

- **Patent Diagram Generator Tool**: Converts patent text into FreeCAD/AutoCAD diagrams
- **ABC_AI**: Smart AI Assistant for Hiring & Task Automation
- **Document Analyzer with OCR + Gemini API**: Chat with PDFs, DOCX, TXT using Tesseract + NLP

## 🤗 Acknowledgments
UdditdocGPT is actively supported by various technologies:
* [Qdrant](https://qdrant.tech/), providing the default vector database
* [LlamaIndex](https://www.llamaindex.ai/), providing the base RAG framework and abstractions

This project has been strongly influenced and supported by other amazing projects like 
[LangChain](https://github.com/hwchase17/langchain),
[GPT4All](https://github.com/nomic-ai/gpt4all),
[LlamaCpp](https://github.com/ggerganov/llama.cpp),
[Chroma](https://www.trychroma.com/)
and [SentenceTransformers](https://www.sbert.net/).

## 📞 Contact
Want to collaborate or hire me for your AI/ML projects? 
- Email: **udditkantsinha2@gmail.com**
- LinkedIn: [lorduddit-](https://linkedin.com/in/lorduddit-/)
- Portfolio: [udditwork.github.io/PORTFOLIO-Uddit](https://udditwork.github.io/PORTFOLIO-Uddit/)
