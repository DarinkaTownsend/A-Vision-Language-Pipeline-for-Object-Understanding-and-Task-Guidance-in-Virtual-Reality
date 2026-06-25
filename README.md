# A Vision-Language Pipeline for Object Understanding and Task Guidance in Virtual Reality

This repository contains the supplementary materials for the paper:

**A Vision-Language Pipeline for Object Understanding and Task Guidance in Virtual Reality**

The project presents a VR-based vision-language assistant that allows users to select objects in a virtual environment, ask natural-language questions, and receive contextual feedback through text, speech, and visual highlighting.

---

## Overview

The system combines a Unity VR environment, voice input, object selection, SAM-based segmentation, and Qwen2.5-VL reasoning. The goal is to support object understanding and task guidance inside a virtual kitchen scenario.

![Environment](Figures/unity_environment2.png)

The prototype allows users to interact with task-relevant objects in a VR kitchen environment. When an object is selected, the system captures the scene, isolates the selected object, processes the user question, and returns a context-aware response.

---

## System Architecture

The framework connects the Unity VR client with a Python backend. Unity handles the VR environment, object selection, scene capture, voice input, and feedback display. The Python backend performs object localization, segmentation, and vision-language reasoning.

![Architecture](Figures/system_architecture.png)

The main pipeline includes:

1. Object selection in the VR scene.
2. Voice-based natural-language question.
3. Scene screenshot capture.
4. Communication with the Python backend.
5. Object localization using the selection box.
6. SAM-based object segmentation.
7. Qwen2.5-VL reasoning.
8. Text, speech, and visual feedback in VR.

---

## Example Interaction

The following images show examples of the interaction flow. The user selects an object, asks a question, and receives feedback from the assistant.

![Interaction](Figures/vr_feedback_sequence.png)

Example questions include:

- “What is this object used for?”
- “Why are the fishes in the sink?”
- “How many pieces should I cut the fish?”
- “What object or action is needed next?”

---

## Visual Processing Pipeline

The system uses the selected object region to generate visual inputs for the vision-language model. The process includes the full scene, selected object crop, binary mask, mask overlay, and segmented object crop.

![Processing](Figures/process_example.png)

This step helps the model focus on the selected object while still preserving the full scene context.

---

## Backend Communication

The Unity application communicates with the Python backend through an HTTPS tunnel. The backend receives the scene image and user question, processes the selected object, and returns a structured JSON response.


![Communication](Figures/ngrok_connection.png)

The returned response may include:

- the generated answer,
- a related object,
- coordinates for visual highlighting in the VR scene.

---

## Evaluation Data

The repository includes participant-level evaluation logs generated during the user study. These files contain the data used to compute the main evaluation metrics.

Included files:

```text
baseline_evaluation_log.xlsx
assisted_evaluation_log.xlsx
```

The evaluation metrics include:

- response accuracy,
- response relevance,
- task completion time,
- number of steps,
- response latency.

---

## Evaluation Results

The assisted condition reduced both task completion time and the number of steps compared with the baseline condition.

![Evaluation 1](Figures/task_completion_time_by_vr_experience.png)
![Evaluation 2](Figures/task_steps_by_vr_experience.png)


The evaluation showed that the assistant helped participants complete the task more efficiently while providing mostly accurate and relevant responses.

---

## Repository Structure

```text
.
├── UnityProject/
│   └── Unity VR application files
├── PythonBackend/
│   └── Backend server and model inference scripts
├── figures/
│   └── Images used in the paper and README
├── evaluation_data/
│   ├── baseline_evaluation_log.xlsx
│   └── assisted_evaluation_log.xlsx
└── README.md
```

---

## Models Used

We use the following models:

- **Segment Anything Model (SAM)** for selected object segmentation.
- **Qwen2.5-VL** for multimodal reasoning and question answering.

---

