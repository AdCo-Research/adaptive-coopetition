# Adaptive Coopetition (AdCo)
Inference-time computation is a critical yet challenging paradigm for enhancing the reasoning performance of large language models (LLMs). While several existing strategies improve reasoning stability and consistency, they suffer from notable limitations: self-correction often reinforces the model's initial biases, and Multi-Agent Collaboration (MAC) often fails due to the lack of efficient coordination mechanisms, leading to collective errors. Although external, high-performing verifiers can detect reasoning errors, making them reliable requires substantial training efforts. To address these challenges, we introduce a novel inference-time multi-round, multi-agent framework in which LLM agents utilize an adaptive, UCB-based 'coopetition' mechanism. At each round, agents leverage coarse verifier signals to determine whether to collaborate or compete, and iteratively refine their reasoning based on peer feedback. Without relying on high-performance verifiers, our adaptive strategy achieves significant performance gains on math reasoning benchmarks, delivering a relative improvement over baselines. Extensive experiments demonstrate that our approach remains robust and consistent in terms of accuracy under different sample sizes and configurations. This adaptive, signal-guided 'coopetition' framework significantly enhances overall reasoning robustness by leveraging diverse prior knowledge and reasoning traces, also promoting uncertainty-driven exploration, especially when participants have comparable capabilities. From this perspective, our work offers a fresh lens on inference-time computation and paves the way for more resilient multi-agent LLM systems.
## Installation
AdCo requires the installation of [AutoGen](https://github.com/microsoft/autogen) and Python (3.10 or later).
## Usage
When running AdCo, the following features can be customized:
- PRM address (`--prm_addr`): set PRM address. 
- Open source model base URL (`--opensource_base_url`): set the base URL for open source model requests (https://api.novita.ai/v3/openai by default).
- Input dataset (`--input`): set the dataset containing question and answer fields, which the AdCo will solve.
- Result output logging (`--output`): set a file in which results will be logged. 
- Question filter (`--filter_output`): when specified, runs only questions previously answered incorrectly.
- Skipping previously answered questions (`--continue_from_checkpoint`): when set, skip already answered questions from the previous run.
- Toggle sampling during critique phase (`--do_sampling`): when set, generate multiple answer samples during the critique phase.
- Parallelism (`--parallelism`): set the number of threads to run (five by default).
- Model list (`--model_list`): set the list of models to run (GPT-4o, DeepSeek-r1, Qwen-QWQ-32b by default).
- Strategy algorithm (`--strategy`): set the strategy algorithm to use—either basic, UCB, competitive, or collaborative (basic by default). 
- Fixed strategy (`--fix_ucb`): toggle whether to fix the used strategy as competitive or collaborative (requires that strategy algorithm is set to UCB).
- Maximum number of questions to run (`--max_num_questions`): set a maximum number (whole number) of questions to run, per runner (no maximum by default).
- Toggle deactivating PRM (`--deact_prm`): if `true`, the PRM score usage is deactivated (this is set to `false` by default).

In order to successfully run AdCo, the __required arguments are `prm_addr`, `input`, `output`, `parallelism`, and `filter_output`__. 

The following API keys should be set in the environment: 
- `API_KEY`: OpenAI API Key
- `OPEN_SOURCE_API_KEY`: Open source API Key
- `PRM_API_KEY`: PRM API Key


## Citation 📖

```bibtex
@inproceedings{awm2024wang,
  title = {Adaptive Coopetition: Leveraging Coarse Verifier Signals for Resilient Multi-Agent LLM Reasoning},
  author = {Rui Jerry Huang, Anastasia Miin, Wendy Yaqiao Liu, Lei Ding},
  journal={The 5th Workshop on Mathematical Reasoning and AI at NeurIPS 2025},
  year = {2025},
}
```
