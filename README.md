# On the synchronization between Hugging Face pre-trained language models and their upstream GitHub repository
The modern development of Pre-trained Language Models (PTLMs) like Llama, GPT, and BERT is a distributed effort, split across two critical platforms. The upstream process, involving writing training code, running experiments, and managing configurations, primarily happens on GitHub (GH). The downstream process, involving model distribution, sharing weights, and enabling user inference, is centered on the Hugging Face (HF) Hub, which now boasts over 2 million pre-trained models.
This separation creates a complex supply chain where the code on GitHub and the models on Hugging Face are intrinsically linked. However, managing the flow of changes between these two platforms presents significant challenges. Model developers and users alike face critical questions:
- **Consistency**: Is the model I'm downloading from HF built from the latest code in the GH repository?
- **Provenance**: Can I trace a HF model version back to the exact training script and configuration that produced it?
- **Timeliness**: When a bug is fixed in the GH training code, how long until a corrected model is available on HF?

Currently, no established practices or tools ensure that these two platforms remain synchronized. This lack of coordination can lead to version drift, where the model on Hugging Face becomes stale, misaligned, or irreproducible from its supposed source code on GitHub, undermining trust and reliability in the ecosystem.
To address this gap, we conducted a large-scale empirical study to understand the current state of synchronization between GitHub and Hugging Face. We employed a mixed-methods approach (quantitative and qualitative analysis) to investigate the commit activities across 325 PTLM families, consisting of 904 HF models and their corresponding GH repositories. Our key observations are discussed below.
## Divergent Roles Revealed by Commit Activities
Our analysis of over 157,000 commits reveals a clear and statistically significant division of labor between the two platforms. Commit activities on GitHub (upstream) are dominated by changes to model structure (29.7%), external documentation (21.0%), and training infrastructure (9.0%). This underscores GH's role as the engine for core development, architectural refinement, and coding the training process.

In contrast, commit activities on Hugging Face (downstream) focus most on external documentation (38.8%), preprocessing (16.6%), and model structure (14.4%). This reflects HF's role as a distribution point, where efforts are concentrated on making models usable through better documentation, tokenizers, and deployment-ready assets.
## Eight Distinct Synchronization Patterns Identified
We investigated how these commit activities align over time. By analyzing the lag (which platform starts first), synchronization type (temporal alignment of commits), and intensity (frequency of activity), we identified eight distinct synchronization patterns. The most prevalent pattern is Disperse Synchronization (39.4%), where activities on the two platforms occur with limited overlap and extended delays, often resulting in one platform continuing development while the other is inactive.

Other patterns range from Frequent Synchronization (2.5%), which indicates well-coordinated, automated workflows, to Rare Disjoint Synchronization (3.7%), where there is virtually no alignment between platforms. The prevalence of patterns with poor synchronization highlights a widespread, structural disconnect in cross-platform release engineering.
## The High Cost of Poor Synchronization
The consequences of these synchronization gaps are tangible. We found that changes made on GitHub take an average of 15.8 days to be reflected on Hugging Face. In the worst-case patterns, such as Sporadic Disjoint Synchronization, this delay can exceed 127 days. Furthermore, synchronization does not necessarily improve with more contributors; larger teams often lead to more fragmented and less coordinated updates across GH and HF.
As PTLM families mature, their synchronization often worsens, shifting from minimal-but-aligned patterns to the fragmented Disperse Synchronization, increasing the risk that users access outdated or inconsistent model versions. These findings establish a critical need for improved tooling and practices to manage the lifecycle of PTLMs across the upstream-downstream divide, ensuring reproducibility, traceability, and user trust.
## Takeaway
Our findings reveal that the synchronization between GitHub and Hugging Face is largely ad-hoc and inefficient, characterized by significant delays and fragmented update patterns. This disconnect poses a direct threat to the reproducibility and reliability of the AI supply chain, as users can easily access models on Hugging Face that are stale or inconsistent with their upstream source code. To build trust and ensure model integrity, the community must develop and adopt better tooling—such as automated CI/CD pipelines and provenance tracking—that explicitly links model artifacts on Hugging Face to the specific code commits on GitHub that produced them.
## Folder Structure
- **Code**: This folder contains all scripts used in the pre-experiment phase, including those for GitHub commit extraction, link extraction from model cards, Hugging Face author and commit extraction, and pattern visualization.
- **RQs**: This folder contains the code for analyzing the three research questions.
- **Dataset**: This folder contains the datasets used for this experiment, including the subsets used for manual analysis.
- **Synchronization Pattern Examples**: This folder contains scatter plot visualizations that depict an example of each identified synchronization pattern, from frequent to rare.
- **Results**: This folder contains all results from our experiment, including the final framework and supporting examples.
- **Other_Files**: This folder contains other relevant and useful files.
## Requirements
Python Programming Language

Python Libraries
- pandas
- github
- request
- beautiful soup
- huggingface_hub
- NLTK
- gemini API
- sklearn
- matplotlib
- scipy
- numpy

DrawIO
## Authors
- Ajibode Adekunle
- Abdul Ali Bangash
- Bram Adams
- Ahmed E. Hassan
