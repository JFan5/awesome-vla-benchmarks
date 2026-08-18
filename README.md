# Awesome VLA Benchmarks [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

[English](README.md) | [简体中文](README.zh-CN.md)

A curated list of benchmarks, evaluation frameworks, and datasets for **Vision-Language-Action (VLA)** models in robotics.

VLA models take visual observations and language instructions as input, and output robot actions. This list catalogs the benchmarks used to evaluate them.

**Contributions welcome!** Please read the [contributing guidelines](CONTRIBUTING.md) before submitting a pull request.

---

## Table of Contents

- [Awesome VLA Models](#awesome-vla-models)
- [Simulation Benchmarks - Manipulation](#simulation-benchmarks---manipulation)
- [Simulation Benchmarks - Embodied AI / Navigation](#simulation-benchmarks---embodied-ai--navigation)
- [Humanoid Benchmarks](#humanoid-benchmarks)
- [Real-World Datasets & Benchmarks](#real-world-datasets--benchmarks)
- [Sim-to-Real Evaluation](#sim-to-real-evaluation)
- [VLA-Specific Evaluation Frameworks](#vla-specific-evaluation-frameworks)
- [Robustness & Safety Benchmarks](#robustness--safety-benchmarks)
- [Unified Platforms](#unified-platforms)
- [Survey Papers](#survey-papers)
- [Related Awesome Lists](#related-awesome-lists)

---

## Awesome VLA Models

A list of published Vision-Language-Action models, grouped by openness first (✓, ◐, ✗) and then sorted in reverse chronological order within each group.

- **VLM Backbone**: the pretrained vision-language model the VLA was built on (or "from-scratch" if none).
- **Action Head**: how continuous robot actions are produced — discrete tokens, diffusion, flow matching, etc.
- **Open**: ✓ if weights/code are publicly released; ◐ if partial (code only / weights restricted); ✗ if closed.

| Model | Date | Org | VLM Backbone | Action Head | Params | Open | Links |
|-------|------|-----|--------------|-------------|--------|------|-------|
| **τ0-VLA** | 2026-08 | SII Research | Vision-language backbone + Mixture-of-Transformers | Hierarchical planner + world-model-guided test-time computation | — | ✓ | [Paper](https://arxiv.org/abs/2608.16885) / [Code](https://github.com/sii-research/tau-0-vla) |
| **TurboVLA** | 2026-07 | H-EmbodVis | Independent vision/language encoders (V+L→A) | Compact decoder; 32 Hz, <1 GB VRAM on RTX 4090 | 0.2B | ✓ | [Paper](https://arxiv.org/abs/2607.27205) / [Code](https://github.com/H-EmbodVis/TurboVLA) |
| **LingBot-VLA 2.0** | 2026-07 | Ant Group / Robbyant | Qwen3-VL-4B-Instruct | MoE action expert, 55-D unified action space | 6B | ✓ | [Code](https://github.com/Robbyant/lingbot-vla-v2) |
| **Wall-OSS-0.5** | 2026-05 | X Square Robot | 3B VLM | Gradient-bridged co-training (discrete + flow matching) | 4B | ✓ | [Paper](https://arxiv.org/abs/2605.30877) / [Code](https://github.com/X-Square-Robot/wall-x) |
| **A1** | 2026-04 | — | Pretrained VLM with implicit affordance priors | Inter-layer truncated flow matching (early exit) | — | ✓ | [Paper](https://arxiv.org/abs/2604.05672) |
| **AR-VLA** | 2026-03 | INSAIT / KU Leuven | Modular VLA perception backbone | Autoregressive continuous action expert | — | ✓ | [Paper](https://arxiv.org/abs/2603.10126) / [Site](https://arvla.insait.ai/) |
| **Ψ₀ (Psi-0)** | 2026-03 | Physical Superintelligence Lab | Decoupled human-video pretraining | Humanoid loco-manipulation post-training | — | ✓ | [Paper](https://arxiv.org/abs/2603.12263) / [Code](https://github.com/physical-superintelligence-lab/Psi0) |
| **Xiaomi-Robotics-0** | 2026-02 | Xiaomi | Cross-embodiment pretrained VLM | Asynchronous execution with timestep alignment | — | ✓ | [Paper](https://arxiv.org/abs/2602.12684) / [Site](https://xiaomi-robotics-0.github.io/) |
| **LAP-3B** | 2026-02 | Princeton / Physical Intelligence | Large VLM | Language-action pretraining | 3B | ✓ | [Paper](https://arxiv.org/abs/2602.10556) / [Site](https://lap-vla.github.io/) |
| **LingBot-VLA** | 2026-01 | Ant Group / Robbyant | Qwen2.5-VL + depth features | Dual-arm action decoder | 4B | ✓ | [Paper](https://arxiv.org/abs/2601.18692) / [Code](https://github.com/Robbyant/lingbot-vla) |
| **InternVLA-A1** | 2026-01 | Shanghai AI Lab (InternRobotics) | Qwen3.5-2B | Unified action expert via shared full-attention layers | — | ✓ | [Paper](https://arxiv.org/abs/2601.02456) / [Code](https://github.com/InternRobotics/InternVLA-A1) |
| **ACoT-VLA** | 2026-01 | AgiBot | Pretrained VLM backbone | Action Chain-of-Thought + flow matching | — | ✓ | [Paper](https://arxiv.org/abs/2601.11404) / [Code](https://github.com/AgibotTech/ACoT-VLA) |
| **Green-VLA** | 2026-01 | Sber Robotics Center | GreenVLA 2B / 5B | Staged multi-embodiment policy + RL alignment | 2B / 5B | ✓ | [Paper](https://arxiv.org/abs/2602.00919) / [Code](https://github.com/greenvla/GreenVLA) |
| **InternVLA-M1** | 2025-10 | Shanghai AI Lab (InternRobotics) | Spatial-grounding pretrained VLM | Spatially guided action post-training | — | ✓ | [Paper](https://arxiv.org/abs/2510.13778) / [Code](https://github.com/InternRobotics/InternVLA-M1) |
| **Galaxea G0** | 2025-09 | Galaxea | Dual-system: VLM planner + VLA executor | Three-stage curriculum (cross-embodiment → single → task) | — | ✓ | [Paper](https://arxiv.org/abs/2509.00576) / [Code](https://github.com/OpenGalaxea/GalaxeaVLA) |
| **EO-1** | 2025-08 | EO-Robotics / IPEC | Interleaved vision-text-action pretraining | Autoregressive decoding + flow-matching denoising | 3B | ✓ | [Paper](https://arxiv.org/abs/2508.21112) / [Code](https://github.com/IPEC-PUBLIC/EO-1) |
| **MolmoAct** | 2025-08 | Allen AI (AI2) | Molmo VLM | Action reasoning + chunked action tokens | 7B | ✓ | [Paper](https://arxiv.org/abs/2508.07917) / [Code](https://github.com/allenai/MolmoAct) |
| **WorldVLA** | 2025-06 | Alibaba DAMO | Chameleon | Unified world-model + action autoregression | 7B | ✓ | [Paper](https://arxiv.org/abs/2506.21539) / [Code](https://github.com/alibaba-damo-academy/WorldVLA) |
| **GR00T N1.5** | 2025-06 | NVIDIA | Eagle-2 VLM | DiT action head (improved post-training) | 2B | ✓ | [Code](https://github.com/NVIDIA/Isaac-GR00T) |
| **SmolVLA** | 2025-06 | Hugging Face | SmolVLM-2 | Flow matching action expert | 450M | ✓ | [Paper](https://arxiv.org/abs/2506.01844) / [Code](https://github.com/huggingface/lerobot) |
| **NORA** | 2025-04 | SUTD | Qwen2.5-VL | FAST tokens | 3B | ✓ | [Paper](https://arxiv.org/abs/2504.19854) / [Code](https://github.com/declare-lab/nora) |
| **GR00T N1** | 2025-03 | NVIDIA | Eagle-2 VLM | DiT action head (System 1+2 design) | 2B | ✓ | [Paper](https://arxiv.org/abs/2503.14734) / [Code](https://github.com/NVIDIA/Isaac-GR00T) |
| **OpenVLA-OFT** | 2025-02 | Stanford | OpenVLA | Parallel decoding + continuous actions + L1 regression | 7B | ✓ | [Paper](https://arxiv.org/abs/2502.19645) / [Code](https://github.com/moojink/openvla-oft) |
| **Magma** | 2025-02 | Microsoft | LLaVA-style | Set-of-marks + action traces | 8B | ✓ | [Paper](https://arxiv.org/abs/2502.13130) / [Code](https://github.com/microsoft/Magma) |
| **DexVLA** | 2025-02 | Midea | Qwen2-VL | Diffusion action expert (dexterous) | 1B+ | ✓ | [Paper](https://arxiv.org/abs/2502.05855) / [Site](https://dex-vla.github.io/) |
| **SpatialVLA** | 2025-01 | Shanghai AI Lab et al. | PaliGemma2 | Ego3D position-aware action tokens | 4B | ✓ | [Paper](https://arxiv.org/abs/2501.15830) / [Code](https://github.com/SpatialVLA/SpatialVLA) |
| **π0-FAST** | 2025-01 | Physical Intelligence | PaliGemma | FAST (DCT) action tokens | 3B | ✓ | [Paper](https://arxiv.org/abs/2501.09747) / [Site](https://www.physicalintelligence.company/research/fast) |
| **CogACT** | 2024-11 | Microsoft Research Asia | OpenVLA-style (DINOv2+SigLIP+Llama2) | DiT action expert (decoupled cognition/action) | 7B+ | ✓ | [Paper](https://arxiv.org/abs/2411.19650) / [Code](https://github.com/microsoft/CogACT) |
| **π0 (Pi-Zero)** | 2024-10 | Physical Intelligence | PaliGemma | Flow-matching action expert | 3B | ✓ | [Paper](https://arxiv.org/abs/2410.24164) / [Code](https://github.com/Physical-Intelligence/openpi) |
| **RDT-1B** | 2024-10 | Tsinghua AIR | SigLIP + T5-XXL | Diffusion Transformer | 1B | ✓ | [Paper](https://arxiv.org/abs/2410.07864) / [Code](https://github.com/thu-ml/RoboticsDiffusionTransformer) |
| **TinyVLA** | 2024-09 | Midea / ECNU | Small VLM (Pythia-based) | Diffusion head | <1B | ✓ | [Paper](https://arxiv.org/abs/2409.12514) / [Site](https://tiny-vla.github.io/) |
| **OpenVLA** | 2024-06 | Stanford / UC Berkeley | Llama-2-7B + DINOv2 + SigLIP | Discrete action tokens (autoregressive) | 7B | ✓ | [Paper](https://arxiv.org/abs/2406.09246) / [Code](https://github.com/openvla/openvla) |
| **Octo** | 2024-05 | UC Berkeley / Stanford | Transformer (from-scratch) | Diffusion head | 27M / 93M | ✓ | [Paper](https://arxiv.org/abs/2405.12213) / [Code](https://github.com/octo-models/octo) |
| **3D-VLA** | 2024-03 | UMass / MIT | 3D-LLM | Generative 3D goal + action | — | ✓ | [Paper](https://arxiv.org/abs/2403.09631) / [Code](https://github.com/UMass-Foundation-Model/3D-VLA) |
| **RoboFlamingo** | 2023-11 | ByteDance / Berkeley | OpenFlamingo | LSTM action head | ~3B | ✓ | [Paper](https://arxiv.org/abs/2311.01378) / [Code](https://github.com/RoboFlamingo/RoboFlamingo) |
| **RT-1** | 2022-12 | Google | EfficientNet + Universal Sentence Encoder | Discrete action tokens (Transformer) | 35M | ✓ | [Paper](https://arxiv.org/abs/2212.06817) / [Code](https://github.com/google-research/robotics_transformer) |
| **AVA-VLA** | 2025-11 | Li Auto DSR | VLA backbone + recurrent state | Active visual attention action policy | 8B | ◐ | [Paper](https://arxiv.org/abs/2511.18960) / [Site](https://liauto-dsr.github.io/AVA-VLA-Page) |
| **GO-1** | 2025-03 | AgiBot | InternVL backbone | Latent planner + action expert (ViLLA) | — | ◐ | [Site](https://agibot-world.com/blog/go1) / [Code](https://github.com/OpenDriveLab/AgiBot-World) |
| **ProgVLA** | 2026-05 | Samsung / KU Leuven | Compact multimodal encoder | Progress-aware flow matching + RL heads | 0.1B | ✗ | [Paper](https://arxiv.org/abs/2605.28231) |
| **X-DiffVLA** | 2026-05 | Peking Univ. et al. | VLA backbone | Cross-embodied diffusion action head | — | ✗ | [Paper](https://arxiv.org/abs/2605.25044) |
| **π0.7** | 2026-04 | Physical Intelligence | π-series backbone | Flow matching + diverse context conditioning (steerable) | — | ✗ | [Paper](https://arxiv.org/abs/2604.15483) / [Site](https://www.pi.website/blog/pi07) |
| **HEX** | 2026-04 | Tsinghua / Huawei et al. | VLM + proprioceptive experts | Flow-matching whole-body action head | — | ✗ | [Paper](https://arxiv.org/abs/2604.07993) |
| **GR00T N2** | 2026-03 | NVIDIA | World action model (post-GR00T N1 architecture) | Joint video + action denoising (world-action paradigm) | — | ✗ | [Site](https://nvidianews.nvidia.com/news/nvidia-and-global-robotics-leaders-take-physical-ai-to-the-real-world) |
| **MMaDA-VLA** | 2026-03 | DAMO / Zhejiang Univ. et al. | MMaDA diffusion backbone | Native discrete diffusion over language/image/action tokens | — | ✗ | [Paper](https://arxiv.org/abs/2603.25406) |
| **DAM-VLA** | 2026-03 | Yonsei Univ. et al. | VLM reasoning module | Routed dynamic diffusion action models | — | ✗ | [Paper](https://arxiv.org/abs/2603.00926) |
| **π*0.6 (Pi-Star 0.6)** | 2025-11 | Physical Intelligence | π0.6 backbone | RECAP: advantage-conditioned RL with experience + corrections | — | ✗ | [Paper](https://arxiv.org/abs/2511.14759) / [Site](https://www.pi.website/blog/pistar06) |
| **X-VLA** | 2025-10 | Tsinghua AIR et al. | Soft-prompted Transformer | Flow-matching cross-embodiment action head | 0.9B | ✗ | [Paper](https://arxiv.org/abs/2510.10274) / [Site](https://thu-air-dream.github.io/X-VLA/) |
| **Gemini Robotics 1.5 / ER 1.5** | 2025-09 | Google DeepMind | Gemini | Thinking VLA + embodied-reasoning planner, cross-embodiment (ER 1.5 via API) | — | ✗ | [Site](https://deepmind.google/blog/gemini-robotics-15-brings-ai-agents-into-the-physical-world/) |
| **Discrete Diffusion VLA** | 2025-08 | Shanghai AI Lab et al. | Single Transformer VLM | Discrete diffusion action decoder | — | ✗ | [Paper](https://arxiv.org/abs/2508.20072) |
| **GR-3** | 2025-07 | ByteDance Seed | Mixture-of-Transformers (VL + action modules) | End-to-end action generation, co-trained with web VL data | 4B | ✗ | [Paper](https://arxiv.org/abs/2507.15493) / [Site](https://seed.bytedance.com/en/blog/seed-research-gr-3-released-a-generalist-robot-model-for-generalization-long-horizon-tasks-and-bi-manual-deformable-object-manipulation) |
| **Gemini Robotics On-Device** | 2025-06 | Google DeepMind | Gemini Nano family | On-device action decoder | — | ✗ | [Site](https://deepmind.google/discover/blog/gemini-robotics-on-device-brings-ai-to-local-robotic-devices/) |
| **π0.5** | 2025-04 | Physical Intelligence | π0 + open-world co-training | Flow matching, generalizes to unseen homes | 3B | ✗ | [Paper](https://arxiv.org/abs/2504.16054) / [Site](https://www.physicalintelligence.company/blog/pi05) |
| **Gemini Robotics** | 2025-03 | Google DeepMind | Gemini 2.0 | Action decoder (closed) | — | ✗ | [Paper](https://arxiv.org/abs/2503.20020) / [Site](https://deepmind.google/discover/blog/gemini-robotics-brings-ai-into-the-physical-world/) |
| **Hi Robot** | 2025-02 | Physical Intelligence | π0 backbone + high-level VLM | Hierarchical (instruction → action) | 3B | ✗ | [Paper](https://arxiv.org/abs/2502.19417) / [Site](https://www.physicalintelligence.company/research/hirobot) |
| **Helix** | 2025-02 | Figure AI | S2 (VLM, ~7B) + S1 (80M visuomotor) | Dual-system, S1 runs at 200Hz | ~7B (S2) | ✗ | [Site](https://www.figure.ai/news/helix) |
| **RT-2-X / RT-X** | 2023-10 | Open X-Embodiment collab | PaLI-X | Discrete action tokens, cross-embodiment | 55B | ✗ | [Paper](https://arxiv.org/abs/2310.08864) / [Site](https://robotics-transformer-x.github.io/) |
| **RT-2** | 2023-07 | Google DeepMind | PaLI-X / PaLM-E | Discrete action tokens (co-fine-tuned with web data) | 5B / 55B | ✗ | [Paper](https://arxiv.org/abs/2307.15818) / [Site](https://robotics-transformer2.github.io/) |
| **PaLM-E** | 2023-03 | Google | PaLM + ViT | LLM-driven planning (text actions) | up to 562B | ✗ | [Paper](https://arxiv.org/abs/2303.03378) / [Site](https://palm-e.github.io/) |

---

## Simulation Benchmarks - Manipulation

| Benchmark | Year | Simulator | Tasks | Key Focus | Links |
|-----------|------|-----------|-------|-----------|-------|
| **ReflexBench** | 2026 | - | Reaction-critical tasks | Fast/predictive manipulation under dynamic disturbances | [Paper](https://arxiv.org/abs/2608.14379) |
| **RoboDojo** | 2026 | Isaac Sim | 42 sim + 18 real tasks | Unified sim-and-real; generalization, memory, precision, long-horizon, open-vocab; 30-policy leaderboard | [Paper](https://arxiv.org/abs/2607.04434) / [Code](https://github.com/RoboDojo-Benchmark/RoboDojo) / [Site](https://robodojo-benchmark.com/) |
| **EBench** | 2026 | Isaac Sim | 26 tasks | Elemental diagnosis: 5 capability x 4 generalization dimensions | [Paper](https://arxiv.org/abs/2606.18239) / [Code](https://github.com/InternRobotics/EBench) |
| **MolmoSpaces** | 2026 | Simulator-agnostic (MuJoCo / Isaac / ManiSkill) | 230K+ envs, 130K assets, 48K manipulable objects | Large-scale open ecosystem + public leaderboard, strong sim-to-real correlation | [Paper](https://arxiv.org/abs/2602.11337) / [Site](https://allenai.github.io/molmospaces/) / [Leaderboard](https://molmospaces.allen.ai/leaderboard) |
| **DOMINO** | 2026 | - | 35 tasks, 110K+ trajs | Dynamic manipulation generalization | [Paper](https://arxiv.org/abs/2603.15620) / [Code](https://github.com/H-EmbodVis/DOMINO) |
| **LiLo-VLA (LIBERO-Long++ / Ultra-Long)** | 2026 | robosuite | 21 tasks | Compositional long-horizon manipulation with object-centric linking | [Paper](https://arxiv.org/abs/2602.21531) |
| **InstructVLA** | 2026 | - | Instruction-tuning suite | Instruction tuning from understanding to manipulation (ICLR 2026) | [Code](https://github.com/InternRobotics/InstructVLA) |
| **GenManip** | 2025 | - | 200 scenarios | LLM-driven instruction generalization | [Paper](https://arxiv.org/abs/2501.03327) / [Code](https://github.com/InternRobotics/GenManip) |
| **PerAct2** | 2024 | CoppeliaSim | 18 bimanual tasks | Bimanual 6-DoF coordination | [Paper](https://arxiv.org/abs/2407.00278) / [Code](https://github.com/markusgrotz/peract_bimanual) |
| **ManiSkill3** | 2024 | SAPIEN | 12 domains | GPU-parallel, fastest sim (30K+ FPS) | [Paper](https://arxiv.org/abs/2410.00425) / [Code](https://github.com/haosulab/ManiSkill) |
| **ManiSkill-HAB** | 2024 | SAPIEN | Home rearrangement | Low-level home manipulation | [Paper](https://arxiv.org/abs/2410.07889) / [Site](https://arth-shukla.github.io/mshab/) |
| **COLOSSEUM** | 2024 | CoppeliaSim | 20 tasks x 14 perturbations | Systematic generalization testing | [Paper](https://arxiv.org/abs/2402.08191) / [Code](https://github.com/robot-colosseum/robot-colosseum) |
| **VLABench** | 2024 | - | 100 categories, 2000+ objects | Long-horizon reasoning | [Paper](https://arxiv.org/abs/2412.18477) / [Code](https://github.com/OpenMOSS/VLABench) |
| **GemBench** | 2024 | CoppeliaSim | 7 primitives x 4 levels | Generalization levels | [Paper](https://arxiv.org/abs/2410.18084) / [Code](https://github.com/vlc-robot/robot-3dlotus) |
| **ClevrSkills** | 2024 | ManiSkill2 | 33 tasks, 330K trajs | Compositional reasoning | [Paper](https://arxiv.org/abs/2404.09187) |
| **RoboCasa** | 2024 | robosuite | 100-365 tasks | Kitchen tasks, generalist robots | [Paper](https://arxiv.org/abs/2406.02523) / [Code](https://github.com/robocasa/robocasa) |
| **BiGym** | 2024 | MuJoCo | 40 tasks | Bimanual mobile manipulation | [Paper](https://arxiv.org/abs/2407.07788) / [Code](https://github.com/chernyadev/bigym) |
| **RoboTwin 2.0** | 2025 | - | 50 dual-arm tasks, 5 embodiments, 731 objects | Scalable data generator + benchmark, 5-axis domain randomization | [Paper](https://arxiv.org/abs/2506.18088) / [Code](https://github.com/RoboTwin-Platform/RoboTwin) |
| **RoboTwin** | 2024 | - | 50 tasks, 5 embodiments | Dual-arm with generative digital twins | [Paper](https://arxiv.org/abs/2409.02920) / [Code](https://github.com/RoboTwin-Platform/RoboTwin) |
| **LIBERO** | 2023 | robosuite | 130 tasks, 4 suites | Lifelong learning, knowledge transfer | [Paper](https://arxiv.org/abs/2306.03310) / [Code](https://github.com/Lifelong-Robot-Learning/LIBERO) |
| **VIMA** | 2023 | PyBullet | 17 task types, 600K+ trajs | Multimodal prompt-conditioned | [Paper](https://arxiv.org/abs/2210.03094) / [Code](https://github.com/vimalabs/VimaBench) |
| **ARNOLD** | 2023 | Isaac Sim | 8 tasks, 40 objects | Continuous states in realistic 3D scenes | [Paper](https://arxiv.org/abs/2304.04321) / [Code](https://github.com/arnold-benchmark/arnold) |
| **LoHoRavens** | 2023 | PyBullet | 10 tasks | Long-horizon without step-by-step instructions | [Paper](https://arxiv.org/abs/2310.12020) / [Code](https://github.com/Shengqiang-Zhang/LoHo-Ravens) |
| **FurnitureBench** | 2023 | Isaac Gym | 8 IKEA-style tasks | Long-horizon furniture assembly | [Paper](https://arxiv.org/abs/2305.12821) / [Code](https://github.com/clvrai/furniture-bench) |
| **DexArt** | 2023 | SAPIEN | Multiple | Dexterous articulated object manipulation | [Paper](https://arxiv.org/abs/2305.05706) / [Code](https://github.com/Kami-code/dexart-release) |
| **CALVIN** | 2022 | PyBullet | 34 tasks, 4 envs | Long-horizon language-conditioned manipulation | [Paper](https://arxiv.org/abs/2112.03227) / [Code](https://github.com/mees/calvin) |
| **Ravens / CLIPort** | 2020/22 | PyBullet | 10 tasks | Transporter / language rearrangement | [Paper](https://arxiv.org/abs/2109.12098) / [Code](https://github.com/google-research/ravens) |
| **BEHAVIOR-1K** | 2022 | OmniGibson | 1000 activities | Full household activities | [Paper](https://arxiv.org/abs/2403.09227) / [Code](https://github.com/StanfordVL/BEHAVIOR-1K) |
| **Bi-DexHands** | 2022 | Isaac Gym | Thousands | Bimanual dexterous manipulation | [Paper](https://arxiv.org/abs/2206.08686) / [Code](https://github.com/PKU-MARL/DexterousHands) |
| **RoboMimic** | 2021 | MuJoCo | 5 sim + 3 real tasks | IL from human demonstrations | [Paper](https://arxiv.org/abs/2108.03298) / [Code](https://github.com/ARISE-Initiative/robomimic) |
| **RLBench** | 2020 | CoppeliaSim | 100 tasks | Vision-guided manipulation (RL, IL, few-shot) | [Paper](https://arxiv.org/abs/1909.12271) / [Code](https://github.com/stepjam/RLBench) |
| **robosuite** | 2020 | MuJoCo | 9 tasks, 10 robots | Modular manipulation framework | [Paper](https://arxiv.org/abs/2009.12293) / [Code](https://github.com/ARISE-Initiative/robosuite) |
| **Meta-World** | 2019 | MuJoCo | 50 tasks | Multi-task / meta RL | [Paper](https://arxiv.org/abs/1910.10897) / [Code](https://github.com/Farama-Foundation/Metaworld) |
| **Franka Kitchen** | 2019 | MuJoCo | 4 subtasks | Multi-task offline RL | [Paper](https://arxiv.org/abs/1910.11956) |

## Simulation Benchmarks - Embodied AI / Navigation

| Benchmark | Year | Simulator | Tasks | Key Focus | Links |
|-----------|------|-----------|-------|-----------|-------|
| **EmbodiedBench** | 2025 | Multi-env | 1,128 instances | MLLM-based embodied agents | [Paper](https://arxiv.org/abs/2504.01850) / [Code](https://github.com/EmbodiedBench/EmbodiedBench) |
| **Habitat 2.0** | 2021 | Habitat Sim | Thousands of envs | Navigation + rearrangement | [Paper](https://arxiv.org/abs/2106.14405) / [Site](https://aihabitat.org/) |
| **AI2-THOR / ManipulaTHOR** | 2017 | Unity | 120+ rooms | Navigation + manipulation | [Paper](https://arxiv.org/abs/1712.05474) / [Code](https://github.com/allenai/ai2thor) |

## Humanoid Benchmarks

| Benchmark | Year | Simulator | Tasks | Key Focus | Links |
|-----------|------|-----------|-------|-----------|-------|
| **SIMPLE** | 2026 | MuJoCo + Isaac Sim | 60 whole-body tasks, 50 scenes, 1000+ objects | Humanoid loco-manipulation policy learning & evaluation; benchmarks IL, VLA and world-action models with zero-shot sim-to-real transfer | [Paper](https://arxiv.org/abs/2606.08278) |
| **WOLF-VLA** | 2026 | - | Instruction-driven locomotion suite | Dynamically consistent whole-body humanoid locomotion VLA benchmark | [Paper](https://arxiv.org/abs/2606.25591) |
| **LeVERB** | 2025 | Isaac Lab | 150+ tasks, 10 categories | Vision-language humanoid whole-body control | [Paper](https://arxiv.org/abs/2506.13751) |
| **Ego Humanoid Manipulation** | 2025 | Isaac Lab | 12 tasks | Egocentric vision humanoid manipulation | [Code](https://github.com/quincy-u/Ego_Humanoid_Manipulation_Benchmark) |
| **HumanoidGen (HGen-Bench)** | 2025 | SAPIEN | 20 tasks | LLM-driven bimanual dexterous task generation | [Paper](https://arxiv.org/abs/2507.00833) / [Code](https://github.com/TeleHuman/HumanoidGen) |
| **Humanoid Everyday** | 2025 | Real-world | 260 tasks, 10.3K trajs | Large-scale real humanoid manipulation | [Paper](https://arxiv.org/abs/2510.08807) / [Data](https://huggingface.co/datasets/USC-GVL/humanoid-everyday) |
| **HumanoidBench** | 2024 | MuJoCo | 27 (15 manip + 12 loco) | Whole-body locomotion & manipulation | [Paper](https://arxiv.org/abs/2403.10506) / [Code](https://github.com/carlosferrazza/humanoid-bench) |
| **OmniH2O** | 2024 | Isaac Gym | 6 tasks | Human-to-humanoid teleoperation & autonomy | [Paper](https://arxiv.org/abs/2406.08858) / [Code](https://github.com/LeCAR-Lab/human2humanoid) |
| **Mimicking-Bench** | 2024 | - | 6 tasks, 23K sequences | Human-to-humanoid scene interaction | [Paper](https://arxiv.org/abs/2412.17730) / [Site](https://mimicking-bench.github.io/) |

## Real-World Datasets & Benchmarks

| Benchmark | Year | Embodiment | Scale | Key Focus | Links |
|-----------|------|------------|-------|-----------|-------|
| **RoboMIND** | 2025 | 4 embodiments | 107K trajs, 479 tasks | Multi-embodiment with failure data | [Paper](https://arxiv.org/abs/2412.13877) / [Site](https://x-humanoid-robomind.github.io/) |
| **AgiBot World** | 2025 | Dual-arm | 1M+ trajs, 217 tasks | Bimanual at scale (4000 m² facility) | [Paper](https://arxiv.org/abs/2503.18899) / [Code](https://github.com/OpenDriveLab/AgiBot-World) |
| **DROID** | 2024 | 18 Frankas | 76K trajs, 564 scenes | In-the-wild manipulation | [Paper](https://arxiv.org/abs/2403.12945) / [Code](https://github.com/droid-dataset/droid_policy_learning) |
| **FMB** | 2024 | Franka | 22.5K demos | Functional manipulation (grasp, assemble) | [Paper](https://arxiv.org/abs/2401.08553) / [Site](https://functional-manipulation-benchmark.github.io/) |
| **RoboVQA** | 2024 | 3 embodiments | 829K pairs | VQA for robot reasoning | [Paper](https://arxiv.org/abs/2311.00899) / [Site](https://robovqa.github.io/) |
| **Open X-Embodiment** | 2023 | 22 robots | 1M+ trajs, 527 skills | Cross-embodiment transfer | [Paper](https://arxiv.org/abs/2310.08864) / [Code](https://github.com/google-deepmind/open_x_embodiment) |
| **BridgeData V2** | 2023 | WidowX 250 | 60K trajs, 24 envs | Multi-task, cross-environment | [Paper](https://arxiv.org/abs/2308.12952) / [Site](https://rail-berkeley.github.io/bridgedata/) |
| **RoboSet** | 2023 | Franka | 7.5K trajs, 38 tasks | Kitchen multi-task | [Paper](https://arxiv.org/abs/2307.01918) / [Site](https://robopen.github.io/roboset/) |
| **Language-Table** | 2023 | Custom | 600K trajs | Open-vocabulary pushing/rearrangement | [Paper](https://arxiv.org/abs/2210.10645) / [Code](https://github.com/google-research/language-table) |
| **LHManip** | 2023 | Real robot | 200 episodes, 20 tasks | Long-horizon in cluttered scenes | [Paper](https://arxiv.org/abs/2312.12036) / [Code](https://github.com/fedeceola/LHManip) |
| **ALOHA / Mobile ALOHA** | 2023 | Custom bimanual | 7-50 tasks | Bimanual (mobile) manipulation | [Paper](https://arxiv.org/abs/2304.13705) / [Site](https://tonyzhaozh.github.io/aloha/) |
| **MUTEX** | 2023 | Franka | 100 sim + 50 real | 6-modality task specification | [Paper](https://arxiv.org/abs/2309.14320) |

## Sim-to-Real Evaluation

| Benchmark | Year | Approach | Key Focus | Links |
|-----------|------|----------|-----------|-------|
| **ArmnetBench v0.1** | 2026 | Low-cost real arm farm | Parallel real-world policy evaluation | [Paper](https://arxiv.org/abs/2607.24481) |
| **VLA-REPLICA** | 2026 | Reproducible real-world rig | Off-the-shelf hardware, in-distribution + OOD evaluation replicable across labs | [Paper](https://arxiv.org/abs/2605.20774) |
| **REALM** | 2025 | Real-validated sim | 15 perturbation factors, p<0.001 correlation | [Paper](https://arxiv.org/abs/2502.02538) / [Code](https://github.com/martin-sedlacek/REALM) |
| **RobotArena Infinity** | 2025 | Real-to-sim translation | VLM scoring + human preferences | [Paper](https://arxiv.org/abs/2504.04603) / [Site](https://robotarenainf.github.io/) |
| **RoboArena** | 2025 | Distributed real eval | Crowd-sourced ELO-style rankings | [Paper](https://arxiv.org/abs/2504.08659) |
| **RoboChallenge** | 2025 | Remote real robots | 30 tasks, fleet of 10 machines | [Paper](https://arxiv.org/abs/2504.01783) / [Site](https://robochallenge.ai/) |
| **SimplerEnv (SIMPLER)** | 2024 | Sim-as-real proxy | Evaluate real-world policies in sim | [Paper](https://arxiv.org/abs/2405.05941) / [Code](https://github.com/simpler-env/SimplerEnv) |

## VLA-Specific Evaluation Frameworks

| Framework | Year | Type | Key Focus | Links |
|-----------|------|------|-----------|-------|
| **vla-eval** | 2026 | Unified harness | 17 benchmarks, 500+ models, Docker-based | [Code](https://github.com/allenai/vla-evaluation-harness) |
| **Eval-Actions + AutoEval** | 2026 | Automated eval | Trustworthy evaluation protocol for robotic manipulation | [Paper](https://arxiv.org/abs/2601.18723) |
| **VLA-Arena** | 2025 | Systematic eval | 170 tasks, 4 dimensions x 3 difficulty levels | [Paper](https://arxiv.org/abs/2504.14064) / [Code](https://github.com/PKU-Alignment/VLA-Arena) |
| **ManipBench** | 2025 | MCQ-based | VLM reasoning for low-level manipulation | [Paper](https://arxiv.org/abs/2504.02452) / [Site](https://manipbench.github.io/) |
| **RoboBench** | 2025 | MCQ/VQA-based | MLLM as embodied brain, 5 cognitive dims | [Paper](https://arxiv.org/abs/2503.19827) / [Site](https://robo-bench.github.io/) |
| **LADEV** | 2024 | Language-driven eval | Auto-generated scenes from NL descriptions | [Paper](https://arxiv.org/abs/2410.05613) |

## Robustness & Safety Benchmarks

| Benchmark | Year | Extends | Key Focus | Links |
|-----------|------|---------|-----------|-------|
| **ReaLM (Red-Teaming)** | 2026 | Physical-world VLMs | Unified red-teaming: 12 attack methods, 3 defenses, 13 VLMs | [Paper](https://arxiv.org/abs/2606.23892) |
| **RedVLA** | 2026 | Multiple | Physical red teaming on real VLA-controlled robots; ASR up to 95.5% on 6 VLAs | [Paper](https://arxiv.org/abs/2604.22591) |
| **LIBERO-X** | 2026 | LIBERO | Hierarchical robustness litmus test | - |
| **LIBERO-Para** | 2026 | LIBERO | Paraphrase robustness (22-52% degradation) | - |
| **RoboMME** | 2026 | Custom | Memory-augmented VLA evaluation | [Code](https://github.com/RoboMME/robomme_benchmark) |
| **RoboCasa-Safety (via OmniGuide)** | 2026 | RoboCasa | Safety-rate protocol (no collision with static furniture) + 3D SDF guidance | [Paper](https://arxiv.org/abs/2603.10052) / [Site](https://omniguide.github.io/) |
| **Linguistic Red-Team** | 2026 | Multiple | Diversity-aware adversarial instructions (SR 93% → 5.85%) | [Paper](https://arxiv.org/abs/2604.05595) |
| **VLSA / AEGIS** | 2026 | Plug-in | Plug-and-play CBF safety-constraint layer with theoretical guarantees | [Paper](https://arxiv.org/abs/2512.11891) |
| **AttackVLA** | 2025 | Multiple | Adversarial + backdoor attack benchmark across the VLA lifecycle; introduces BackdoorVLA | [Paper](https://arxiv.org/abs/2511.12149) |
| **LIBERO-PRO** | 2025 | LIBERO | Robustness under 4-dim perturbations | [Paper](https://arxiv.org/abs/2502.18985) / [Code](https://github.com/Zxy-MLlab/LIBERO-PRO) |
| **LIBERO-Plus** | 2025 | LIBERO | 7-dim x 5-level robustness analysis | [Paper](https://arxiv.org/abs/2503.16064) / [Code](https://github.com/sylvestf/LIBERO-plus) |
| **SimX-OR** | 2025 | Plug-in | Observational robustness (blur, noise, etc.) | [Paper](https://arxiv.org/abs/2504.12453) / [Code](https://github.com/LiHaoHN/SimX-OR) |
| **Eva-VLA** | 2025 | LIBERO | Adversarial physical variations | [Paper](https://arxiv.org/abs/2501.01370) |
| **VLA-Risk** | 2025 | Multiple | Safety/risk across 296 scenarios, 3 dims (object/action/space) x 2 modalities | [OpenReview](https://openreview.net/forum?id=31EjDFwFEe) |
| **Safety-CHORES / SafeVLA** | 2025 | AI2-THOR / CHORES | 5 cost categories (corner, blind_spot, fragile, critical, danger) on long-horizon nav+manip; safe RL via CMDP (NeurIPS 2025 Spotlight) | [Paper](https://arxiv.org/abs/2503.03480) / [Code](https://github.com/PKU-Alignment/SafeVLA) / [Site](https://pku-safevla.github.io/) |

## Unified Platforms

| Platform | Year | Key Focus | Links |
|----------|------|-----------|-------|
| **StarVLA** | 2026 | Lego-like codebase spanning LIBERO, SimplerEnv, RoboTwin 2.0, RoboCasa GR1, BEHAVIOR-1K | [Paper](https://arxiv.org/abs/2604.05014) |
| **RoboVerse** | 2025 | Cross-simulator unified platform (MetaSim) | [Paper](https://arxiv.org/abs/2504.09837) / [Code](https://github.com/RoboVerseOrg/RoboVerse) |
| **STAR-Gen** | 2025 | Generalization taxonomy (visual, semantic, behavioral) | [Paper](https://arxiv.org/abs/2503.11106) / [Site](https://stargen-taxonomy.github.io/) |

## Survey Papers

- **"Vision-Language-Action Models for Robotics: A Review"** - [Site](https://vla-survey.github.io/)
- **"Pure Vision Language Action (VLA) Models: A Comprehensive Survey"** - [Paper](https://arxiv.org/abs/2509.19012)
- **"A Survey on Vision-Language-Action Models for Embodied AI"** - [Paper](https://arxiv.org/abs/2405.14093)
- **"A Survey on Efficient Vision-Language-Action Models"** - [Paper](https://arxiv.org/abs/2510.24795) / [Site](https://evla-survey.github.io/)
- **"A Survey on Vision-Language-Action Models: An Action Tokenization Perspective"** - [Paper](https://arxiv.org/abs/2507.01925)
- **"Benchmarking the Generality of Vision-Language-Action Models"** - [Paper](https://arxiv.org/abs/2512.11315)
- **"Vision-Language-Action in Robotics: A Survey of Datasets, Benchmarks, and Data Engines"** - [Paper](https://arxiv.org/abs/2604.23001)
- **"Vision-Language-Action Safety: Threats, Challenges, Evaluations, and Mechanisms"** - [Paper](https://arxiv.org/abs/2604.23775)
- **"Safety in Embodied AI: A Survey of Risks, Attacks, and Defenses"** - [Paper](https://arxiv.org/abs/2605.02900)
- **"Efficient Vision-Language-Action Models for Embodied Manipulation: A Systematic Survey"** - [Paper](https://arxiv.org/abs/2510.17111)
- **"An Anatomy of Vision-Language-Action Models: From Modules to Milestones and Challenges"** - [Paper](https://arxiv.org/abs/2512.11362)

## Related Awesome Lists

- [Awesome-VLA](https://github.com/LukeLIN-web/Awesome-VLA) - VLA models, benchmarks, datasets
- [awesome-world-models-for-vla-agents](https://github.com/FutureTwT/awesome-world-models-for-vla-agents) - World models for VLA agents
- [awesome-embodied-vla-va-vln](https://github.com/jonyzhang2023/awesome-embodied-vla-va-vln) - VLA, VA, VLN state-of-the-art
- [Awesome-VLA-Papers](https://github.com/Psi-Robot/Awesome-VLA-Papers) - Action tokenization perspective
- [awesome-physical-ai](https://github.com/keon/awesome-physical-ai) - Physical AI, VLA, world models
- [Awesome-VLA-Robotics](https://github.com/Jiaaqiliu/Awesome-VLA-Robotics) - Comprehensive VLA papers
- [Awesome-RL-VLA](https://github.com/Denghaoyuan123/Awesome-RL-VLA) - RL + VLA
- [Awesome-VLA (yueen-ma)](https://github.com/yueen-ma/Awesome-VLA) - 400+ papers visualized
- [Awesome-Learning-for-Manipulation](https://github.com/Noietch/Awesome-Learning-for-Manipulation) - VLA, visuomotor, world models

---

## Contributing

Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)
