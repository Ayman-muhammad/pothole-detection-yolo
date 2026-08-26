# 🚧 Pothole Detection & Tracking using YOLO

> **AI-powered road-surface analysis using custom YOLO object detection, ByteTrack tracking, OpenCV video processing, and a Streamlit web interface.**

A computer vision application for detecting potholes in road imagery and videos, tracking detections across frames, and presenting the results through an interactive web interface.

The system combines **YOLO-based object detection**, **ByteTrack object tracking**, **OpenCV video processing**, and **Streamlit** to create an end-to-end pothole analysis workflow.

---

## 📌 Overview

Potholes are a major road-infrastructure and transportation problem. They can:

- Damage vehicles
- Increase maintenance costs
- Create safety hazards
- Reduce road quality
- Increase accident risk
- Make road-condition monitoring difficult

Traditional road inspection can be time-consuming and expensive.

This project explores how **computer vision and deep learning** can assist with automated pothole detection from road imagery and video.

The application allows a user to:

1. Upload a road video
2. Configure detection parameters
3. Run YOLO-based pothole detection
4. Track detections across video frames
5. Visualize the processed result
6. Download the resulting video

---

# 🎯 Project Goals

The primary goals of the system are:

- Detect potholes automatically using computer vision
- Apply a YOLO object-detection model to road imagery
- Track pothole detections across video frames
- Assign tracking identities to detections
- Process road videos using OpenCV
- Provide an accessible Streamlit interface
- Allow configurable detection parameters
- Produce downloadable processed videos
- Establish a foundation for future road-condition analytics

---

# 🧠 System Architecture

The application follows an end-to-end computer vision pipeline:

```text
                    USER
                     │
                     ▼
             ┌───────────────┐
             │ Streamlit UI  │
             └───────┬───────┘
                     │
                     ▼
             ┌───────────────┐
             │ Video Upload  │
             └───────┬───────┘
                     │
                     ▼
             ┌───────────────┐
             │ OpenCV Reader │
             └───────┬───────┘
                     │
                     ▼
             ┌───────────────┐
             │ YOLO Detector │
             └───────┬───────┘
                     │
                     ▼
             ┌───────────────┐
             │   ByteTrack   │
             │    Tracker    │
             └───────┬───────┘
                     │
                     ▼
             ┌───────────────┐
             │ Frame Drawing │
             │ + Annotations │
             └───────┬───────┘
                     │
                     ▼
             ┌───────────────┐
             │ Output Video  │
             └───────┬───────┘
                     │
             ┌───────┴────────┐
             ▼                ▼
       Visualization       Download
```

---

# 🔬 Computer Vision Pipeline

The overall workflow can be represented as:

```text
Input Video
     │
     ▼
Frame Extraction
     │
     ▼
YOLO Inference
     │
     ▼
Pothole Bounding Boxes
     │
     ▼
Confidence Filtering
     │
     ▼
ByteTrack Association
     │
     ▼
Tracking IDs
     │
     ▼
Annotated Frames
     │
     ▼
Processed Video
```

This architecture separates the major responsibilities of the system:

- **YOLO** → detection
- **ByteTrack** → temporal tracking
- **OpenCV** → video processing
- **Streamlit** → user interaction

---

# 🧩 Core Components

## 1. YOLO Object Detection

The system uses a YOLO-based object-detection model to identify potholes within individual video frames.

For each frame, the detector can produce:

```text
Bounding Box
     +
Class
     +
Confidence Score
```

Conceptually:

```text
Frame
  │
  ▼
YOLO Model
  │
  ├── Bounding Box
  ├── Class
  └── Confidence
```

The detection threshold can be adjusted through the application interface.

---

# 🔄 2. ByteTrack Tracking

Object detection operates independently on individual frames.

Tracking introduces temporal continuity.

```text
Frame 1       Frame 2       Frame 3
   │             │             │
   ▼             ▼             ▼
Pothole       Pothole       Pothole
   │             │             │
   └─────────────┼─────────────┘
                 │
                 ▼
             Track ID
```

ByteTrack associates detections between frames and allows the application to maintain tracking identities.

This makes it possible to follow a detected pothole as the camera moves through the road scene.

---

# 🎥 3. OpenCV Video Processing

OpenCV is responsible for the video-processing layer.

Typical responsibilities include:

- Opening uploaded videos
- Reading frames
- Processing frames sequentially
- Drawing detection results
- Writing processed frames
- Managing video properties
- Producing an output video

Conceptually:

```text
Input Video
     │
     ▼
OpenCV
     │
     ├── Read Frame
     │
     ├── Process Frame
     │
     ├── Annotate Frame
     │
     └── Write Frame
             │
             ▼
       Output Video
```

---

# 🖥️ 4. Streamlit Interface

The application includes a Streamlit interface designed to make the computer vision pipeline accessible without requiring users to interact directly with the Python implementation.

The interface supports the core workflow:

```text
Upload Video
     ↓
Configure Parameters
     ↓
Start Processing
     ↓
Monitor Processing
     ↓
View Result
     ↓
Download Output
```

Potential configuration parameters include:

- Detection confidence
- Image size
- Input video
- Processing settings

---

# 📂 Repository Structure

The current repository is organized around the following core files:

```text
pothole-detection-yolo/
│
├── .gitignore
│
├── best (16).pt
│   └── Trained YOLO model weights
│
├── pothole-detection.ipynb
│   └── Computer vision / model development notebook
│
├── requirements.txt
│   └── Python dependencies
│
├── ui.py
│   └── Streamlit application
│
└── README.md
    └── Project documentation
```

> The repository structure may evolve as the application is further modularized.

---

# 🛠️ Technology Stack

| Technology | Role |
|---|---|
| **Python** | Core programming language |
| **YOLO** | Object detection |
| **Ultralytics** | YOLO implementation and inference |
| **OpenCV** | Video processing |
| **ByteTrack** | Object tracking |
| **Streamlit** | Web interface |
| **Jupyter Notebook** | Model experimentation |
| **Git** | Version control |
| **GitHub** | Source-code hosting |

---

# ⚙️ Requirements

The project requires a Python environment capable of installing the dependencies specified in:

```text
requirements.txt
```

Recommended environment:

```text
Python 3.x
```

Additional requirements may include:

- Sufficient RAM for video processing
- CPU capable of running model inference
- GPU acceleration where available
- FFmpeg/video codecs depending on the environment

---

# 🚀 Installation

## 1. Clone the repository

```bash
git clone https://github.com/Ayman-muhammad/pothole-detection-yolo.git
```

Enter the project directory:

```bash
cd pothole-detection-yolo
```

---

## 2. Create a virtual environment

### Windows

```bash
python -m venv .venv
```

Activate:

```bash
.venv\Scripts\activate
```

### Linux / macOS

```bash
python3 -m venv .venv
```

Activate:

```bash
source .venv/bin/activate
```

---

## 3. Install dependencies

```bash
pip install --upgrade pip
```

Then:

```bash
pip install -r requirements.txt
```

---

# ▶️ Running the Application

Start the Streamlit application with:

```bash
streamlit run ui.py
```

Streamlit will provide a local address similar to:

```text
http://localhost:8501
```

Open the address in a browser.

---

# 🧪 Application Workflow

## Step 1 — Upload

Upload a supported road video through the Streamlit interface.

```text
User
 │
 ▼
Upload Road Video
```

---

## Step 2 — Configure Detection

Adjust available parameters such as:

```text
Confidence Threshold
Image Size
```

These parameters can affect the balance between detection sensitivity and false positives.

---

## Step 3 — Process

The system processes the video frame-by-frame.

```text
Video
  ↓
Frame
  ↓
YOLO
  ↓
Detection
  ↓
ByteTrack
  ↓
Tracking
  ↓
Annotation
  ↓
Next Frame
```

---

## Step 4 — Visualize

The processed video contains the generated detection and tracking annotations.

Depending on the implementation, annotations may include:

```text
Pothole
Confidence
Track ID
Bounding Box
```

---

## Step 5 — Download

The resulting processed video can be downloaded from the application.

---

# 📊 Model Development

The computer vision workflow follows a conventional object-detection lifecycle:

```text
Data
 │
 ▼
Dataset Preparation
 │
 ▼
Annotation
 │
 ▼
Training
 │
 ▼
Validation
 │
 ▼
Evaluation
 │
 ▼
Experimentation
 │
 ▼
Model Selection
 │
 ▼
Deployment
```

Model development can involve experimentation with:

- Training epochs
- Image resolution
- Batch size
- Confidence thresholds
- Data augmentation
- Learning-rate configuration
- Model architecture
- Dataset quality

---

# 📚 Dataset Considerations

Pothole detection is highly dependent on dataset quality.

A robust dataset should ideally contain variation in:

- Pothole size
- Pothole depth
- Road type
- Weather
- Lighting
- Camera angle
- Camera distance
- Road material
- Traffic conditions
- Image quality

A diverse dataset helps reduce overfitting to a narrow visual environment.

---

# 🧪 Model Evaluation

A production-oriented pothole detector should be evaluated using appropriate object-detection metrics.

Important metrics include:

### Precision

Measures how many predicted potholes are actually potholes.

```text
Precision =
True Positives
-----------------------------
True Positives + False Positives
```

### Recall

Measures how many actual potholes were successfully detected.

```text
Recall =
True Positives
-----------------------------
True Positives + False Negatives
```

### IoU

Intersection over Union measures bounding-box overlap.

```text
IoU =
Area of Intersection
-------------------
Area of Union
```

### mAP

Mean Average Precision provides a broader object-detection performance measure.

Future iterations should document actual evaluation results rather than relying only on qualitative observations.

---

# 🧠 Engineering Lessons

This project provides practical experience across several areas of machine learning engineering.

### Computer Vision

- Object detection
- Bounding boxes
- Image preprocessing
- Video inference
- Tracking

### Machine Learning

- Dataset preparation
- Model training
- Evaluation
- Hyperparameter experimentation
- Model optimization

### Software Engineering

- Python application development
- File handling
- Application architecture
- Dependency management
- Error handling

### User-Facing AI

- Streamlit application development
- Upload workflows
- Interactive configuration
- Result visualization
- Downloadable outputs

### Development Workflow

- Git
- GitHub
- Virtual environments
- Dependency management
- Iterative debugging

---

# ⚠️ Known Challenges

Real-world pothole detection introduces several challenges.

## Lighting Variation

Detection performance can change under:

- Bright sunlight
- Shadows
- Night conditions
- Rain
- Low visibility

---

## Pothole Appearance

Potholes vary significantly in:

- Shape
- Size
- Color
- Depth
- Texture

Some road damage may also visually resemble potholes.

---

## Camera Motion

Road videos may contain:

- Camera shake
- Motion blur
- Changing camera angles
- Rapid movement

These conditions can make detection and tracking more difficult.

---

## False Positives

Road features such as:

- Cracks
- Shadows
- Road patches
- Drainage structures
- Surface markings

can potentially be confused with potholes.

---

# 🔐 Responsible AI Considerations

This system is intended as a computer vision research and engineering project.

Detection results should not automatically be treated as authoritative infrastructure assessments.

For real-world deployment, additional validation would be required.

Potential production requirements include:

- Model benchmarking
- Geographic validation
- False-positive analysis
- False-negative analysis
- Dataset governance
- Monitoring
- Model versioning
- Human verification
- Performance monitoring

---

# 🚀 Future Development Roadmap

## Phase 1 — Core Detection

- [x] YOLO-based detection
- [x] Video processing
- [x] Streamlit interface
- [x] Configurable detection
- [x] Processed video output

---

## Phase 2 — Advanced Analytics

- [ ] Image-based pothole detection
- [ ] Detection statistics
- [ ] Confidence distribution
- [ ] Pothole count analytics
- [ ] Frame-level detection metrics
- [ ] Processing performance metrics

---

## Phase 3 — Geospatial Intelligence

- [ ] GPS integration
- [ ] Pothole coordinate extraction
- [ ] Interactive pothole map
- [ ] Geographic clustering
- [ ] Road-condition heatmaps

Conceptually:

```text
Camera
  │
  ▼
Pothole Detection
  │
  ▼
GPS Coordinate
  │
  ▼
Database
  │
  ▼
Map
  │
  ▼
Road Condition Dashboard
```

---

## Phase 4 — Infrastructure Intelligence

Future versions could explore:

- [ ] Pothole severity estimation
- [ ] Pothole size estimation
- [ ] Road-condition scoring
- [ ] Automated reports
- [ ] Maintenance prioritization
- [ ] Historical road-condition tracking

---

## Phase 5 — Production Platform

Potential production capabilities include:

```text
Mobile Camera
      │
      ▼
Edge / Cloud Inference
      │
      ▼
Detection API
      │
      ▼
Pothole Database
      │
      ▼
Analytics Platform
      │
      ▼
Infrastructure Dashboard
```

Potential deployment targets could include:

- Web applications
- Mobile applications
- Edge devices
- Cloud inference services
- Road-inspection systems

---

# 📈 Long-Term Vision

The long-term concept extends beyond detecting potholes in individual videos.

The broader objective is to explore a **road-condition intelligence platform**.

```text
                   ROAD INTELLIGENCE
                          │
        ┌─────────────────┼─────────────────┐
        │                 │                 │
        ▼                 ▼                 ▼
    Detection          Location          Severity
        │                 │                 │
        └─────────────────┼─────────────────┘
                          │
                          ▼
                   Road Database
                          │
                          ▼
                  Analytics Engine
                          │
                          ▼
               Infrastructure Dashboard
```

Such a system could eventually assist organizations with:

- Road inspection
- Maintenance planning
- Infrastructure monitoring
- Geographic analysis
- Road-condition reporting

---

# 🏗️ Production Architecture — Future

A production-scale version could evolve toward:

```text
                    ┌──────────────────┐
                    │   Web / Mobile   │
                    │     Clients      │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │   API Gateway    │
                    └────────┬─────────┘
                             │
              ┌──────────────┼──────────────┐
              ▼              ▼              ▼
        Detection API   Media Service   Auth Service
              │              │              │
              └──────────────┼──────────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ Inference Engine │
                    │   YOLO + Tracker │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ Data / Metadata  │
                    │     Storage      │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ Analytics Layer  │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ Admin Dashboard  │
                    └──────────────────┘
```

---

# ⚡ Performance Considerations

Video inference can be computationally expensive.

Potential optimization strategies include:

- GPU acceleration
- Model quantization
- Reduced image resolution
- Frame skipping
- Batch inference where appropriate
- Efficient video codecs
- Asynchronous processing
- Background workers
- Model optimization
- Edge inference

Performance should be measured rather than optimized based solely on assumptions.

Useful metrics include:

```text
FPS
Latency / Frame
Processing Time
CPU Usage
GPU Usage
Memory Usage
Video Duration
Inference Time
```

---

# 🧪 Recommended Testing Strategy

Future engineering improvements should introduce automated testing around:

### Unit Tests

Test:

- Configuration handling
- Input validation
- Utility functions
- Detection-processing logic

### Integration Tests

Test:

- Video processing
- Model loading
- Tracking integration
- Output generation

### Application Tests

Test:

- File upload
- Configuration
- Processing
- Output availability
- Download workflow

---

# 📋 Definition of Done

A future feature should be considered complete when:

```text
[ ] Implementation complete
[ ] Input validation implemented
[ ] Error handling implemented
[ ] Security reviewed
[ ] Tested locally
[ ] Regression checked
[ ] Documentation updated
[ ] Dependencies reviewed
[ ] Performance considered
[ ] Git history reviewed
```

---

# 🔒 Security & Privacy

The application may process user-uploaded video files.

Production deployments should therefore consider:

- File-type validation
- File-size limits
- Temporary-file cleanup
- Safe filenames
- Access control
- Upload isolation
- Resource limits
- Dependency security
- Secure deployment configuration

Uploaded files should not be retained longer than necessary.

---

# 🗂️ Git Workflow

Recommended development workflow:

```bash
git status
```

Create a feature branch:

```bash
git checkout -b feature/new-detection-analytics
```

Stage changes:

```bash
git add .
```

Commit:

```bash
git commit -m "feat: add detection analytics"
```

Push:

```bash
git push -u origin feature/new-detection-analytics
```

---

# 📝 Commit Convention

Recommended commit prefixes:

```text
feat:
fix:
docs:
refactor:
test:
perf:
security:
chore:
```

Examples:

```bash
git commit -m "feat: add pothole statistics"

git commit -m "fix: handle invalid video uploads"

git commit -m "perf: optimize video inference"

git commit -m "docs: improve project documentation"

git commit -m "security: validate uploaded video files"
```

---

# 📦 Model Files

The repository currently contains a trained model file:

```text
best (16).pt
```

Large model artifacts should be evaluated before being committed directly to Git history.

For larger production models, consider:

- Git LFS
- Model registries
- Object storage
- Release artifacts

Do not commit credentials, private datasets, or other sensitive artifacts.

---

# ⚠️ Model and Dataset Attribution

This repository contains computer-vision/model assets and implementation material that may originate from prior project work.

Any redistribution or reuse should respect:

- Original repository licensing
- Dataset licensing
- Model licensing
- Third-party dependencies
- Original author attribution requirements

This repository should not be interpreted as a claim of ownership over third-party datasets, models, or code.

Where this implementation has been modified or extended, those changes should be documented clearly.

---

# 👨‍💻 Author

## Ekalale Lokaale (Ayman)

**Computer Science | Artificial Intelligence | Machine Learning | Computer Vision | Full-Stack Engineering**

Interested in building practical intelligent systems that combine:

- Artificial Intelligence
- Machine Learning
- Computer Vision
- Software Engineering
- Data
- Automation
- Secure digital platforms

---

# 🎓 Engineering Focus

This project represents practical work across:

```text
Artificial Intelligence
        +
Computer Vision
        +
Machine Learning
        +
Python Engineering
        +
Video Processing
        +
Object Tracking
        +
Web Application Development
```

---

# 🌍 Project Vision

The goal is to move from a simple computer-vision demonstration toward systems capable of solving real-world infrastructure problems.

```text
Computer Vision
       ↓
Object Detection
       ↓
Tracking
       ↓
Geospatial Intelligence
       ↓
Infrastructure Analytics
       ↓
Decision Support
```

---

# ⭐ Project

**Pothole Detection & Tracking using YOLO**

Built with:

```text
Python
YOLO
Ultralytics
OpenCV
ByteTrack
Streamlit
```

---

## 👨‍💻 Ekalale Lokaale (Ayman)

> **Building intelligent systems for real-world problems.**

---

<p align="center">

**🚧 Detect. Track. Analyze. Improve Roads.**

</p>
