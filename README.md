# Awesome VLA Benchmarks [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

A curated list of benchmarks, evaluation frameworks, and datasets for **Vision-Language-Action (VLA)** models in robotics.

VLA models take visual observations and language instructions as input, and output robot actions. This list catalogs the benchmarks used to evaluate them.

**Contributions welcome!** Please read the [contributing guidelines](CONTRIBUTING.md) before submitting a pull request.

---

## Table of Contents

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

## Simulation Benchmarks - Manipulation

| Benchmark | Year | Simulator | Tasks | Key Focus | Links |
|-----------|------|-----------|-------|-----------|-------|
| **CALVIN** | 2022 | PyBullet | 34 tasks, 4 envs | Long-horizon language-conditioned manipulation | [Paper](https://arxiv.org/abs/2112.03227) / [Code](https://github.com/mees/calvin) |
| **LIBERO** | 2023 | robosuite | 130 tasks, 4 suites | Lifelong learning, knowledge transfer | [Paper](https://arxiv.org/abs/2306.03310) / [Code](https://github.com/Lifelong-Robot-Learning/LIBERO) |
| **RLBench** | 2020 | CoppeliaSim | 100 tasks | Vision-guided manipulation (RL, IL, few-shot) | [Paper](https://arxiv.org/abs/1909.12271) / [Code](https://github.com/stepjam/RLBench) |
| **PerAct2** | 2024 | CoppeliaSim | 18 bimanual tasks | Bimanual 6-DoF coordination | [Paper](https://arxiv.org/abs/2407.00278) / [Code](https://github.com/markusgrotz/peract_bimanual) |
| **Meta-World** | 2019 | MuJoCo | 50 tasks | Multi-task / meta RL | [Paper](https://arxiv.org/abs/1910.10897) / [Code](https://github.com/Farama-Foundation/Metaworld) |
| **ManiSkill3** | 2024 | SAPIEN | 12 domains | GPU-parallel, fastest sim (30K+ FPS) | [Paper](https://arxiv.org/abs/2410.00425) / [Code](https://github.com/haosulab/ManiSkill) |
| **ManiSkill-HAB** | 2024 | SAPIEN | Home rearrangement | Low-level home manipulation | [Paper](https://arxiv.org/abs/2410.07889) / [Site](https://arth-shukla.github.io/mshab/) |
| **robosuite** | 2020 | MuJoCo | 9 tasks, 10 robots | Modular manipulation framework | [Paper](https://arxiv.org/abs/2009.12293) / [Code](https://github.com/ARISE-Initiative/robosuite) |
| **RoboMimic** | 2021 | MuJoCo | 5 sim + 3 real tasks | IL from human demonstrations | [Paper](https://arxiv.org/abs/2108.03298) / [Code](https://github.com/ARISE-Initiative/robomimic) |
| **VIMA** | 2023 | PyBullet | 17 task types, 600K+ trajs | Multimodal prompt-conditioned | [Paper](https://arxiv.org/abs/2210.03094) / [Code](https://github.com/vimalabs/VimaBench) |
| **Ravens / CLIPort** | 2020/22 | PyBullet | 10 tasks | Transporter / language rearrangement | [Paper](https://arxiv.org/abs/2109.12098) / [Code](https://github.com/google-research/ravens) |
| **ARNOLD** | 2023 | Isaac Sim | 8 tasks, 40 objects | Continuous states in realistic 3D scenes | [Paper](https://arxiv.org/abs/2304.04321) / [Code](https://github.com/arnold-benchmark/arnold) |
| **COLOSSEUM** | 2024 | CoppeliaSim | 20 tasks x 14 perturbations | Systematic generalization testing | [Paper](https://arxiv.org/abs/2402.08191) / [Code](https://github.com/robot-colosseum/robot-colosseum) |
| **VLABench** | 2024 | - | 100 categories, 2000+ objects | Long-horizon reasoning | [Paper](https://arxiv.org/abs/2412.18477) / [Code](https://github.com/OpenMOSS/VLABench) |
| **GemBench** | 2024 | CoppeliaSim | 7 primitives x 4 levels | Generalization levels | [Paper](https://arxiv.org/abs/2410.18084) / [Code](https://github.com/vlc-robot/robot-3dlotus) |
| **ClevrSkills** | 2024 | ManiSkill2 | 33 tasks, 330K trajs | Compositional reasoning | [Paper](https://arxiv.org/abs/2404.09187) |
| **LoHoRavens** | 2023 | PyBullet | 10 tasks | Long-horizon without step-by-step instructions | [Paper](https://arxiv.org/abs/2310.12020) / [Code](https://github.com/Shengqiang-Zhang/LoHo-Ravens) |
| **BEHAVIOR-1K** | 2022 | OmniGibson | 1000 activities | Full household activities | [Paper](https://arxiv.org/abs/2403.09227) / [Code](https://github.com/StanfordVL/BEHAVIOR-1K) |
| **RoboCasa** | 2024 | robosuite | 100-365 tasks | Kitchen tasks, generalist robots | [Paper](https://arxiv.org/abs/2406.02523) / [Code](https://github.com/robocasa/robocasa) |
| **GenManip** | 2025 | - | 200 scenarios | LLM-driven instruction generalization | [Paper](https://arxiv.org/abs/2501.03327) / [Code](https://github.com/InternRobotics/GenManip) |
| **Franka Kitchen** | 2019 | MuJoCo | 4 subtasks | Multi-task offline RL | [Paper](https://arxiv.org/abs/1910.11956) |
| **FurnitureBench** | 2023 | Isaac Gym | 8 IKEA-style tasks | Long-horizon furniture assembly | [Paper](https://arxiv.org/abs/2305.12821) / [Code](https://github.com/clvrai/furniture-bench) |
| **BiGym** | 2024 | MuJoCo | 40 tasks | Bimanual mobile manipulation | [Paper](https://arxiv.org/abs/2407.07788) / [Code](https://github.com/chernyadev/bigym) |
| **RoboTwin** | 2024 | - | 50 tasks, 5 embodiments | Dual-arm with generative digital twins | [Paper](https://arxiv.org/abs/2409.02920) / [Code](https://github.com/RoboTwin-Platform/RoboTwin) |
| **DexArt** | 2023 | SAPIEN | Multiple | Dexterous articulated object manipulation | [Paper](https://arxiv.org/abs/2305.05706) / [Code](https://github.com/Kami-code/dexart-release) |
| **Bi-DexHands** | 2022 | Isaac Gym | Thousands | Bimanual dexterous manipulation | [Paper](https://arxiv.org/abs/2206.08686) / [Code](https://github.com/PKU-MARL/DexterousHands) |
| **DOMINO** | 2026 | - | 35 tasks, 110K+ trajs | Dynamic manipulation generalization | [Paper](https://arxiv.org/abs/2603.15620) / [Code](https://github.com/H-EmbodVis/DOMINO) |
| **LiLo-VLA (LIBERO-Long++ / Ultra-Long)** | 2026 | robosuite | 21 tasks | Compositional long-horizon manipulation with object-centric linking | [Paper](https://arxiv.org/abs/2602.21531) |
| **InstructVLA** | 2026 | - | Instruction-tuning suite | Instruction tuning from understanding to manipulation (ICLR 2026) | [Code](https://github.com/InternRobotics/InstructVLA) |

## Simulation Benchmarks - Embodied AI / Navigation

| Benchmark | Year | Simulator | Tasks | Key Focus | Links |
|-----------|------|-----------|-------|-----------|-------|
| **AI2-THOR / ManipulaTHOR** | 2017 | Unity | 120+ rooms | Navigation + manipulation | [Paper](https://arxiv.org/abs/1712.05474) / [Code](https://github.com/allenai/ai2thor) |
| **Habitat 2.0** | 2021 | Habitat Sim | Thousands of envs | Navigation + rearrangement | [Paper](https://arxiv.org/abs/2106.14405) / [Site](https://aihabitat.org/) |
| **EmbodiedBench** | 2025 | Multi-env | 1,128 instances | MLLM-based embodied agents | [Paper](https://arxiv.org/abs/2504.01850) / [Code](https://github.com/EmbodiedBench/EmbodiedBench) |

## Humanoid Benchmarks

| Benchmark | Year | Simulator | Tasks | Key Focus | Links |
|-----------|------|-----------|-------|-----------|-------|
| **HumanoidBench** | 2024 | MuJoCo | 27 (15 manip + 12 loco) | Whole-body locomotion & manipulation | [Paper](https://arxiv.org/abs/2403.10506) / [Code](https://github.com/carlosferrazza/humanoid-bench) |
| **LeVERB** | 2025 | Isaac Lab | 150+ tasks, 10 categories | Vision-language humanoid whole-body control | [Paper](https://arxiv.org/abs/2506.13751) |
| **Ego Humanoid Manipulation** | 2025 | Isaac Lab | 12 tasks | Egocentric vision humanoid manipulation | [Code](https://github.com/quincy-u/Ego_Humanoid_Manipulation_Benchmark) |
| **HumanoidGen (HGen-Bench)** | 2025 | SAPIEN | 20 tasks | LLM-driven bimanual dexterous task generation | [Paper](https://arxiv.org/abs/2507.00833) / [Code](https://github.com/TeleHuman/HumanoidGen) |
| **Humanoid Everyday** | 2025 | Real-world | 260 tasks, 10.3K trajs | Large-scale real humanoid manipulation | [Paper](https://arxiv.org/abs/2510.08807) / [Data](https://huggingface.co/datasets/USC-GVL/humanoid-everyday) |
| **OmniH2O** | 2024 | Isaac Gym | 6 tasks | Human-to-humanoid teleoperation & autonomy | [Paper](https://arxiv.org/abs/2406.08858) / [Code](https://github.com/LeCAR-Lab/human2humanoid) |
| **SIMPLE** (Psi-0) | 2026 | MuJoCo + Isaac Sim | 6+ loco-manip tasks | Open humanoid VLA benchmarking simulator | [Paper](https://arxiv.org/abs/2603.12263) / [Code](https://github.com/physical-superintelligence-lab/Psi0) |
| **Mimicking-Bench** | 2024 | - | 6 tasks, 23K sequences | Human-to-humanoid scene interaction | [Paper](https://arxiv.org/abs/2412.17730) / [Site](https://mimicking-bench.github.io/) |

## Real-World Datasets & Benchmarks

| Benchmark | Year | Embodiment | Scale | Key Focus | Links |
|-----------|------|------------|-------|-----------|-------|
| **Open X-Embodiment** | 2023 | 22 robots | 1M+ trajs, 527 skills | Cross-embodiment transfer | [Paper](https://arxiv.org/abs/2310.08864) / [Code](https://github.com/google-deepmind/open_x_embodiment) |
| **BridgeData V2** | 2023 | WidowX 250 | 60K trajs, 24 envs | Multi-task, cross-environment | [Paper](https://arxiv.org/abs/2308.12952) / [Site](https://rail-berkeley.github.io/bridgedata/) |
| **DROID** | 2024 | 18 Frankas | 76K trajs, 564 scenes | In-the-wild manipulation | [Paper](https://arxiv.org/abs/2403.12945) / [Code](https://github.com/droid-dataset/droid_policy_learning) |
| **RoboMIND** | 2025 | 4 embodiments | 107K trajs, 479 tasks | Multi-embodiment with failure data | [Paper](https://arxiv.org/abs/2412.13877) / [Site](https://x-humanoid-robomind.github.io/) |
| **AgiBot World** | 2025 | Dual-arm | 1M+ trajs, 217 tasks | Bimanual at scale (4000 m² facility) | [Paper](https://arxiv.org/abs/2503.18899) / [Code](https://github.com/OpenDriveLab/AgiBot-World) |
| **RoboSet** | 2023 | Franka | 7.5K trajs, 38 tasks | Kitchen multi-task | [Paper](https://arxiv.org/abs/2307.01918) / [Site](https://robopen.github.io/roboset/) |
| **Language-Table** | 2023 | Custom | 600K trajs | Open-vocabulary pushing/rearrangement | [Paper](https://arxiv.org/abs/2210.10645) / [Code](https://github.com/google-research/language-table) |
| **FMB** | 2024 | Franka | 22.5K demos | Functional manipulation (grasp, assemble) | [Paper](https://arxiv.org/abs/2401.08553) / [Site](https://functional-manipulation-benchmark.github.io/) |
| **LHManip** | 2023 | Real robot | 200 episodes, 20 tasks | Long-horizon in cluttered scenes | [Paper](https://arxiv.org/abs/2312.12036) / [Code](https://github.com/fedeceola/LHManip) |
| **ALOHA / Mobile ALOHA** | 2023 | Custom bimanual | 7-50 tasks | Bimanual (mobile) manipulation | [Paper](https://arxiv.org/abs/2304.13705) / [Site](https://tonyzhaozh.github.io/aloha/) |
| **RoboVQA** | 2024 | 3 embodiments | 829K pairs | VQA for robot reasoning | [Paper](https://arxiv.org/abs/2311.00899) / [Site](https://robovqa.github.io/) |
| **MUTEX** | 2023 | Franka | 100 sim + 50 real | 6-modality task specification | [Paper](https://arxiv.org/abs/2309.14320) |

## Sim-to-Real Evaluation

| Benchmark | Year | Approach | Key Focus | Links |
|-----------|------|----------|-----------|-------|
| **SimplerEnv (SIMPLER)** | 2024 | Sim-as-real proxy | Evaluate real-world policies in sim | [Paper](https://arxiv.org/abs/2405.05941) / [Code](https://github.com/simpler-env/SimplerEnv) |
| **REALM** | 2025 | Real-validated sim | 15 perturbation factors, p<0.001 correlation | [Paper](https://arxiv.org/abs/2502.02538) / [Code](https://github.com/martin-sedlacek/REALM) |
| **RobotArena Infinity** | 2025 | Real-to-sim translation | VLM scoring + human preferences | [Paper](https://arxiv.org/abs/2504.04603) / [Site](https://robotarenainf.github.io/) |
| **RoboArena** | 2025 | Distributed real eval | Crowd-sourced ELO-style rankings | [Paper](https://arxiv.org/abs/2504.08659) |
| **RoboChallenge** | 2025 | Remote real robots | 30 tasks, fleet of 10 machines | [Paper](https://arxiv.org/abs/2504.01783) / [Site](https://robochallenge.ai/) |

## VLA-Specific Evaluation Frameworks

| Framework | Year | Type | Key Focus | Links |
|-----------|------|------|-----------|-------|
| **vla-eval** | 2026 | Unified harness | 17 benchmarks, 500+ models, Docker-based | [Code](https://github.com/allenai/vla-evaluation-harness) |
| **VLA-Arena** | 2025 | Systematic eval | 170 tasks, 4 dimensions x 3 difficulty levels | [Paper](https://arxiv.org/abs/2504.14064) / [Code](https://github.com/PKU-Alignment/VLA-Arena) |
| **LADEV** | 2024 | Language-driven eval | Auto-generated scenes from NL descriptions | [Paper](https://arxiv.org/abs/2410.05613) |
| **ManipBench** | 2025 | MCQ-based | VLM reasoning for low-level manipulation | [Paper](https://arxiv.org/abs/2504.02452) / [Site](https://manipbench.github.io/) |
| **RoboBench** | 2025 | MCQ/VQA-based | MLLM as embodied brain, 5 cognitive dims | [Paper](https://arxiv.org/abs/2503.19827) / [Site](https://robo-bench.github.io/) |
| **Eval-Actions + AutoEval** | 2026 | Automated eval | Trustworthy evaluation protocol for robotic manipulation | [Paper](https://arxiv.org/abs/2601.18723) |

## Robustness & Safety Benchmarks

| Benchmark | Year | Extends | Key Focus | Links |
|-----------|------|---------|-----------|-------|
| **LIBERO-PRO** | 2025 | LIBERO | Robustness under 4-dim perturbations | [Paper](https://arxiv.org/abs/2502.18985) / [Code](https://github.com/Zxy-MLlab/LIBERO-PRO) |
| **LIBERO-Plus** | 2025 | LIBERO | 7-dim x 5-level robustness analysis | [Paper](https://arxiv.org/abs/2503.16064) / [Code](https://github.com/sylvestf/LIBERO-plus) |
| **LIBERO-X** | 2026 | LIBERO | Hierarchical robustness litmus test | - |
| **LIBERO-Para** | 2026 | LIBERO | Paraphrase robustness (22-52% degradation) | - |
| **SimX-OR** | 2025 | Plug-in | Observational robustness (blur, noise, etc.) | [Paper](https://arxiv.org/abs/2504.12453) / [Code](https://github.com/LiHaoHN/SimX-OR) |
| **Eva-VLA** | 2025 | LIBERO | Adversarial physical variations | [Paper](https://arxiv.org/abs/2501.01370) |
| **VLA-Risk** | 2025 | Multiple | Safety/risk across 296 scenarios | [Paper](https://arxiv.org/abs/2502.09622) |
| **RoboMME** | 2026 | Custom | Memory-augmented VLA evaluation | [Code](https://github.com/RoboMME/robomme_benchmark) |
| **Safety-CHORES / SafeVLA** | 2025 | AI2-THOR / CHORES | 5 cost categories (corner, blind_spot, fragile, critical, danger) on long-horizon nav+manip; safe RL via CMDP (NeurIPS 2025 Spotlight) | [Paper](https://arxiv.org/abs/2503.03480) / [Code](https://github.com/PKU-Alignment/SafeVLA) / [Site](https://pku-safevla.github.io/) |
| **RoboCasa-Safety (via OmniGuide)** | 2026 | RoboCasa | Safety-rate protocol (no collision with static furniture) + 3D SDF guidance | [Paper](https://arxiv.org/abs/2603.10052) / [Site](https://omniguide.github.io/) |
| **Linguistic Red-Team** | 2026 | Multiple | Diversity-aware adversarial instructions (SR 93% → 5.85%) | [Paper](https://arxiv.org/abs/2604.05595) |
| **VLSA / AEGIS** | 2026 | Plug-in | Plug-and-play CBF safety-constraint layer with theoretical guarantees | [Paper](https://arxiv.org/abs/2512.11891) |

## Unified Platforms

| Platform | Year | Key Focus | Links |
|----------|------|-----------|-------|
| **RoboVerse** | 2025 | Cross-simulator unified platform (MetaSim) | [Paper](https://arxiv.org/abs/2504.09837) / [Code](https://github.com/RoboVerseOrg/RoboVerse) |
| **STAR-Gen** | 2025 | Generalization taxonomy (visual, semantic, behavioral) | [Paper](https://arxiv.org/abs/2503.11106) / [Site](https://stargen-taxonomy.github.io/) |

## Survey Papers

- **"Vision-Language-Action Models for Robotics: A Review"** - [Site](https://vla-survey.github.io/)
- **"Pure Vision Language Action (VLA) Models: A Comprehensive Survey"** - [Paper](https://arxiv.org/abs/2509.19012)
- **"A Survey on Vision-Language-Action Models for Embodied AI"** - [Paper](https://arxiv.org/abs/2405.14093)
- **"A Survey on Efficient Vision-Language-Action Models"** - [Paper](https://arxiv.org/abs/2510.24795) / [Site](https://evla-survey.github.io/)
- **"A Survey on Vision-Language-Action Models: An Action Tokenization Perspective"** - [Paper](https://arxiv.org/abs/2507.01925)
- **"Benchmarking the Generality of Vision-Language-Action Models"** - [Paper](https://arxiv.org/abs/2512.11315)

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
