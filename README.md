# ImpressionGPT

This code implements ImpressionGPT in our paper:

Chong Ma, Zihao Wu, Jiaqi Wang, Shaochen Xu, Yaonai Wei, Zhengliang Liu, Xi Jiang, Lei Guo, Xiaoyan Cai, Shu Zhang, Tuo Zhang, Dajiang Zhu, Dinggang Shen, Tianming Liu, Xiang Li

[ImpressionGPT: An Iterative Optimizing Framework for Radiology Report Summarization with ChatGPT](https://arxiv.org/abs/2304.08448).

# Update

[2024.02.12] This work has been published in IEEE Transactions on Artificial Intelligence.

[An Iterative Optimizing Framework for Radiology Report Summarization with ChatGPT](https://ieeexplore.ieee.org/abstract/document/10433180).


<div align="center">
    <img src="/res/pipeline.png">
</div>


# Abstract

The 'Impression' section of a radiology report is a critical basis for communication between radiologists and other physicians, and it is typically written by radiologists based on the 'Findings' section. However, writing numerous impressions can be laborious and error-prone for radiologists. Although recent studies have achieved promising results in automatic impression generation using large-scale medical text data for pre-training and fine-tuning pre-trained language models, such models often require substantial amounts of medical text data and have poor generalization performance. While large language models (LLMs) like ChatGPT have shown strong generalization capabilities and performance, their performance in specific domains, such as radiology, remains under-investigated and potentially limited. To address this limitation, we propose ImpressionGPT, which leverages the in-context learning capability of LLMs by constructing dynamic contexts using domain-specific, individualized data. This dynamic prompt approach enables the model to learn contextual knowledge from semantically similar examples from existing data. Additionally, we design an iterative optimization algorithm that performs automatic evaluation on the generated impression results and composes the corresponding instruction prompts to further optimize the model. The proposed ImpressionGPT model achieves state-of-the-art performance on both MIMIC-CXR and OpenI datasets without requiring additional training data or fine-tuning the LLMs. This work presents a paradigm for localizing LLMs that can be applied in a wide range of similar application scenarios, bridging the gap between general-purpose LLMs and the specific language processing needs of various domains.


# Dynamic Prompt

We construct the dynamic context in prompt with similar reports. These similar reports is selected from a report corpus based on the label extracted by a report labeler.

<div align="center">
    <img src="/res/dynamic_prompt.png">
</div>


# Iterative Prompt

Based on the dynamic promot, we introduce an iterative prompt, which used in the iterative optimization algorithm with good and bad responses obtaind from ChatGPT.

<div align="center">
    <img src="/res/Iterative_prompt.png">
</div>


# Usage

**1. Dataset.**

You should first download the [MIMIC-CXR-Reports](https://physionet.org/content/mimic-cxr/2.0.0/) and [OpenI-Reports](https://openi.nlm.nih.gov/imgs/collections/NLMCXR_reports.tgz) datasets.

Note that you should get a License before you download the MIMIC data. 
Or you can visit my post-processing data in this repo [radiology-report-extraction](https://github.com/MoMarky/radiology-report-extraction).


**2. Install environment.**

Run the code "package install" and input your OpenAI key.


**3. Define the main functions.**

Run "chestGPT_summary_near_sample_with_interactive_v6", "random_sample_selection_v2", and "random_sample_selection_v2_for_openI".


**4. Change data path and begin.**

Please run the code with the title "One Good And N Bad", which is the optimal setup for our work.

Change the path of "root, train_data, train_label_space, df_test_csv, test_label_space".



# Citation

If you use this code, or otherwise found our work valuable, please cite:

###
    @article{ma2024iterative,
      title={An Iterative Optimizing Framework for Radiology Report Summarization with ChatGPT},
      author={Ma, Chong and Wu, Zihao and Wang, Jiaqi and Xu, Shaochen and Wei, Yaonai and Liu, Zhengliang and Zeng, Fang and Jiang, Xi and Guo, Lei and Cai, Xiaoyan and others},
      journal={IEEE Transactions on Artificial Intelligence},
      year={2024},
      publisher={IEEE}
    }











