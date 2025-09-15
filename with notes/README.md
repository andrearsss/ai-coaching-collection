Pose Trainer: Correcting Exercise Posture using Pose Estimation, Stanford University (https://arxiv.org/pdf/2006.11718)
[Jun 2020]
- Built a small dataset of correct and incorrect form guided by personal trainers
- OpenPose for keypoints estimation
- Keypoint Normalization based on torso's length to account different bodies and distances from the camera
- 1. Geometric evaluation: heuristics (angles) for each different exercise
- 2. Machine Learning evaluation: Dynamic Time Warping model + KNN to measure non-linear similarity between two time series (uses dynamic programming to find match between observed series and desired series) and a median filter for noise robustness. Then, KNN to classify 'correct' vs 'incorrect'
- Output is textual but deterministic, based on which angle exceeds the range
- Idea: show the user its skeleton against a ground truth skeleton




AIFit: Automatic 3D Human-Interpretable Feedback Models for Fitness Training, Romanian Academy and Lund University (https://tinyurl.com/aifitmodel)
[2021]
- Large scale dataset, Fit3D, containing over 3 million images and corresponding 3d human shape and motion capture ground truth configurations, with over 37 repeated exercises performed by instructors and trainees. Made with complex motion capture system
- 3D pose estimation to compute angular features and apply thresholds
- Output in natural language but deterministic




PoseFix: Correcting 3D Human Poses with Natural Language, University of Catalonia (https://arxiv.org/pdf/2309.08480)
[Sep 2023]
- Tackles the reverse problem of correcting a 3D character's pose using natural language prompts
- PoseFix dataset: tuples made of (source 3D pose, target 3D pose, text feedback to get from source to target pose)




What to Say and When to Say it: Live Fitness Coaching as a Testbed for Situated Interaction, Qualcomm AI Research and University of California San Diego (https://arxiv.org/pdf/2407.08101)
[Jul 2024]
- Overcomes the limitations of existing SOTA Vision-Language Model implementing asynchronous interactions instead of the typical prompt-based/turn-based interaction. They propose a novel architecture, STREAM-VLM, that can decide on-the-fly when and what to say to the user
- Stream-VLM architecture: 3D CNN over frames + LLaMA-2-7B for attention layers + special tokens to decide whether to give feedback at each instant. Features from the vision backbone are fused into the LM backbone through cross attention at several layers following the methodology of [4, 11].
- They built the Qualcomm Exercise Video Dataset for this purpose (https://www.qualcomm.com/developer/software/qevd-dataset)
- Training: 3D CNN pretrained on ImageNet and fine-tuned on QEVD-Fit-300K short-clips. Then, the model is trained on fitness questions and feedback annotations (QEVD-Fit-Coach, excluding long-range clips) to align the CNN and the LM (only cross-attention layer weights are updated). Finally, the model is fine-tuned on long-range clips from QEVD-Fit-Coach with textual feedbacks interleaved. The LLaMA-2 language backbone is fine-tuned using LoRA (dim=32) with the 3D CNN and adapter (cross-attention layer) weights kept frozen.




Rehabilitation Exercise Quality Assessment and Feedback Generation Using Large Language Models with Prompt Engineering, University of Toronto and Kuwait (https://arxiv.org/html/2505.18412v1)
[May 2025]
- Proposes a framework that enables pretrained LLMs to evaluate rehabilitation exercise quality by using raw body joint sequence or a set of exercise-specific features extracted from the joints (angles, pelvis stability etc.), along with prompt engineering techniques like zero-shot Chain-of-Thought, Certainty elicitation etc.
- Uses UI-PRMD and REHAB24-6 data sets




FormCoach: Lift Smarter, Not Harder, University of Pennsylvania and Max Planck Institute for Intelligent Systems (https://arxiv.org/pdf/2508.07501)
[Aug 2025]
- They use a VLM to analyze frames along with user preferences (such as "focus on my knees alignment") to detect form deviations. As the user begins an exercise, the app synchronizes frames from the live feed with frames from an expert reference for a real-time side-by-side visual comparison. When discrepancies appear, the app responds with a textual feedback, optionally delivered via text-to-speech.
- They used Fit3D for evaluation, a dataset made of pairs of recordings of identical exercises executed by an instructor (expert) and a trainee (beginner). They employed expert annotators to add concise (<15 words) actionable corrections that compare the paired movements.
- LLM-based evalutation metrics: they experimented with various VLMs and used GPT4.1 as an evaluator. They provided GPT4.1 with the annotated feedbacks and the model's feedback and asked to rate them on various aspects (accuracy, actionability and hallucination). Not clear why GPT4.1 is also in the results table together with the tested models if it has been used as an evaluator.
- Result: very low accuracy, some hallucinations




UniPose: A Unified Multimodal Framework for Human
Pose Comprehension, Generation and Editing (https://arxiv.org/pdf/2411.16781?)
[2025]

- To do



