## On the synchronization between Hugging Face pre-trained language models and their upstream GitHub repository
The modern development of Pre-trained Language Models (PTLMs) like Llama, GPT, and BERT is a distributed effort, split across two critical platforms. The upstream process, involving writing training code, running experiments, and managing configurations, primarily happens on GitHub (GH). The downstream process, involving model distribution, sharing weights, and enabling user inference, is centered on the Hugging Face (HF) Hub, which now boasts over 2 million pre-trained models.

This separation creates a complex supply chain where the code on GitHub and the models on Hugging Face are intrinsically linked. However, managing the flow of changes between these two platforms presents significant challenges. Model developers and users alike face critical questions:
- **Consistency**: Is the model I'm downloading from HF built from the latest code in the GH repository?
- **Provenance**: Can I trace a HF model version back to the exact training script and configuration that produced it?
- **Timeliness**: When a bug is fixed in the GH training code, how long until a corrected model is available on HF?
