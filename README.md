# CargoIQ - AI-Powered Cargo Intelligence & Risk Analysis System

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![PyTorch](https://img.shields.io/badge/PyTorch-2.0%2B-ee4c2c)
![Streamlit](https://img.shields.io/badge/Streamlit-Dashboard-red)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Prototype-orange)
![GPU](https://img.shields.io/badge/GPU-RTX%204050-blueviolet)

## 🎯 Overview

CargoIQ is an innovative AI-driven prototype developed to revolutionize customs and border security operations. Designed for efficiency and accuracy, this system analyzes cargo and X-ray images to provide intelligent decision support for customs officers, significantly enhancing their ability to detect contraband, misdeclarations, and security threats.

At its core, CargoIQ leverages advanced object detection to identify items within cargo imagery. Crucially, it's built to function even without a fully integrated, locally-trained model by utilizing a sophisticated **simulation mode**, allowing for comprehensive demonstration and testing in diverse environments.

The system's intelligence capabilities are multifaceted:
1.  **Misdeclaration Detection:** By semantically matching detected objects against declared cargo manifests, CargoIQ flags discrepancies, indicating potential fraud or errors.
2.  **Concealment Detection:** It identifies suspicious patterns, unusual groupings, or materials commonly used to hide illicit goods, providing early warnings of attempted concealment.
3.  **Anomaly Detection:** Critical for security, it flags restricted, prohibited, or otherwise anomalous items (e.g., weapons, drugs, oversized quantities) that require immediate attention.

Beyond detection, CargoIQ features a **context-aware risk engine** that calculates a normalized risk score (0-100). This score is dynamic, factoring in detection confidence, the severity of identified issues (mismatch, concealment, anomaly), and contextual multipliers (e.g., high-frequency detections, multiple concurrent issues). This holistic approach ensures a precise risk assessment.

The system culminates in a user-friendly **Streamlit dashboard** where officers can upload multiple cargo images, input declared items, and instantly visualize detailed analysis results, including object frequencies, confidence levels, and specific findings. Most importantly, it provides clear explanations for risk scores and actionable recommendations, guiding officers on whether to release, review, inspect, hold, or alert authorities about a shipment.

Built with a modular and robust architecture, CargoIQ is a production-ready prototype, showcasing rapid AI integration for critical real-world applications, capable of operating entirely offline on standard hardware (e.g., an RTX 4050).

## 🚀 Approach: Solving Cargo Intelligence Challenges

CargoIQ addresses the complex problem of manual and time-consuming cargo inspection by adopting a multi-layered AI and software architecture approach:

1.  **AI-Powered Vision:** At its foundation, the system uses pre-trained (or simulated) object detection models to "see" and identify items within cargo images. This automates the primary inspection step, reducing human error and improving throughput.
2.  **Intelligent Data Aggregation & Analysis:** Detections from multiple images are aggregated, allowing for holistic analysis across an entire shipment. Frequency analysis, confidence handling, and semantic matching convert raw detections into meaningful intelligence.
3.  **Rule-Based Intelligence Modules:** Specialized modules (Misdeclaration, Concealment, Anomaly) operate on the aggregated data. These modules use defined rules and semantic understanding to identify specific risk patterns, mirroring the analytical steps an expert customs officer would take.
4.  **Context-Aware Risk Assessment:** A sophisticated risk engine combines the findings from all intelligence modules. It not only assigns base risk scores but also dynamically adjusts them using context multipliers (e.g., increasing risk if multiple issues are found, or if an anomaly is detected with high confidence). This provides a nuanced and explainable overall risk score.
5.  **Explainable AI & Decision Support:** Unlike black-box AI systems, CargoIQ generates human-readable explanations for every finding and the final risk score. Based on this, a decision advisory module provides concrete, actionable recommendations for customs officers, ranging from "Release" to "Immediate Alert," complete with suggested follow-up steps and documentation requirements.
6.  **User-Centric Interface:** A Streamlit dashboard provides an intuitive gateway to this complex system, making the powerful AI accessible to non-technical users. It streamlines the input process (image upload, declared cargo) and presents results clearly, enabling quick, informed decisions.

By integrating these components, CargoIQ provides a comprehensive, transparent, and actionable solution to the critical challenge of cargo security.

## ✨ Key Features

-   **AI-Powered Object Detection**: Identify items in cargo/X-ray images using either a provided model or a robust simulation.
-   **Multi-Image Processing**: Analyze multiple images simultaneously, aggregating detections across all inputs.
-   **Intelligent Caching**: Avoid re-computation for identical images, speeding up repeated analyses.
-   **Semantic Matching**: Understands relationships between detected and declared items (e.g., "laptop" matches "electronics").
-   **Misdeclaration Detection**: Flags discrepancies between physical contents and declared manifests.
-   **Concealment Detection**: Identifies suspicious arrangements indicative of hidden items.
-   **Anomaly Detection**: Alerts to restricted, prohibited, or unusual items/quantities.
-   **Context-Aware Risk Scoring**: Generates a dynamic 0-100 risk score based on detection confidence, issue severity, and contextual factors.
-   **Decision Support**: Provides clear, actionable recommendations (e.g., "Release", "Inspect", "Alert") with detailed reasoning.
-   **Streamlit Dashboard**: Intuitive web interface for easy interaction, image upload, and result visualization.
-   **Offline Operation**: Fully functional without internet access or external APIs, ideal for secure environments.
-   **GPU Acceleration**: Leverages NVIDIA GPUs (like RTX 4050) for faster inference (when a real model is used).

## 🏗️ Project Structure
CargoIQ/
├── app/
│ ├── main.py # Main application entry point
│ ├── config.py # Global configuration settings
│ ├── models/ # Object detection model handling (loading, inference, caching)
│ │ ├── detector.py # Model loading/inference logic
│ │ ├── inference.py # Batch inference engine
│ │ └── cache.py # Inference caching layer
│ ├── intelligence/ # Core AI intelligence modules
│ │ ├── mismatch.py # Misdeclaration detection
│ │ ├── concealment.py # Concealment detection
│ │ ├── anomaly.py # Anomaly detection
│ │ ├── rules.py # Business rules engine for intelligence
│ │ └── semantic_matcher.py # Maps declared to detected items
│ ├── analytics/ # Data analysis components
│ │ └── frequency.py # Object frequency analysis
│ ├── risk_engine/ # Risk scoring and context analysis
│ │ ├── scorer.py # Final risk score calculation
│ │ └── context.py # Context multiplier calculation
│ ├── explainability/ # Human-readable explanation generation
│ │ └── generator.py # Generates detailed analysis reports
│ ├── decision/ # Decision support and recommendations
│ │ └── advisor.py # Provides actionable advice
│ ├── services/ # Pipeline orchestration and data aggregation
│ │ ├── pipeline.py # Orchestrates the entire analysis flow
│ │ └── aggregator.py # Combines detections from multiple images
│ ├── schemas/ # Data validation schemas
│ │ └── request_schema.py
│ ├── constants/ # Static rules, mappings, and thresholds
│ │ ├── rules.py
│ │ └── mappings.py
│ ├── utils/ # Common utilities
│ │ ├── logger.py
│ │ ├── hashing.py
│ │ └── image_utils.py
│ └── ui/ # Streamlit dashboard interface
│ └── dashboard.py
├── data/ # Runtime data (managed by .gitignore)
│ ├── input_images/
│ ├── outputs/
│ ├── logs/
│ └── cache/
├── modelweights/ # Pre-trained model files (managed by .gitignore)
│ ├── cascade_mask_rcnn_r101_with_RoR1.pth
│ └── ddod_r101_with_RoR1.pth
├── requirements.txt
├── run.py
└── README.md

text


## 🚀 Quick Start

### Prerequisites

-   Python 3.8 or higher
-   `pip` package manager
-   **NVIDIA GPU** with CUDA drivers (e.g., RTX 4050) for optimal GPU acceleration. If no GPU or CUDA is configured, the system will seamlessly run in CPU mode and leverage its robust simulation capabilities.

### Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/YOUR_GITHUB_USERNAME/CargoIQ.git
    cd CargoIQ
    ```

2.  **Install Python dependencies:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: .\venv\Scripts\activate
    pip install -r requirements.txt
    ```

    **For CUDA support on NVIDIA GPUs:**
    ```bash
    pip uninstall torch torchvision -y
    pip install torch torchvision --index-url https://download.pytorch.org/whl/cu121
    ```

3.  **Setup project directories:**
    ```bash
    python setup_cargoiq_full.py
    ```

4.  **Acquire Model Weights (Required for Real Detection):**

    > 💡 **Note:** CargoIQ includes a robust **simulation mode** that allows the entire system to function perfectly for demonstration purposes even without model files. Skip this step if you only need a quick demo.

    - **Download `model_weights.zip` from Google Drive:**

      👉 [Download model_weights.zip from Google Drive](YOUR_GOOGLE_DRIVE_LINK_HERE)

    - **Extract and rename the folder:**

      After downloading, extract `model_weights.zip`. You will get a folder called `model_weights`. **Rename this folder to `modelweights`** (remove the underscore).

      On Windows:
      ```
      Right-click the extracted folder → Rename → type "modelweights"
      ```

      On Mac/Linux:
      ```bash
      mv model_weights modelweights
      ```

    - **Place it in the project root:**

      Move or copy the renamed `modelweights` folder into the root of the `CargoIQ/` project directory so the structure looks like this:

      ```
      CargoIQ/
      ├── modelweights/
      │   ├── cascade_mask_rcnn_r101_with_RoR1.pth   ← (752.8 MB)
      │   └── ddod_r101_with_RoR1.pth                ← (410.7 MB)
      ├── app/
      ├── data/
      ├── run.py
      └── ...
      ```

    The system will automatically detect and load `ddod_r101_with_RoR1.pth` (prioritized for RTX 4050 performance).

### Running the Application

#### Option 1: Streamlit Dashboard (Recommended)

```bash
python run.py
If you encounter torch.classes related errors, use:

Bash

streamlit run app/ui/dashboard.py --server.fileWatcherType none --server.headless true
Then open your browser at http://localhost:8501

Option 2: Command Line
Bash

# Simulate analysis (no images needed)
python run.py --analyze --num-images 5 --declared electronics clothing

# Analyze a directory of images
python run.py --analyze --image-dir data/input_images --declared electronics documents
💻 Usage Guide (Streamlit Dashboard)
Open your browser to http://localhost:8501

Upload Cargo Images: Use the file uploader to select multiple X-ray or cargo images (.png, .jpg, etc.)

Enter Declared Cargo: Type declared items (e.g., laptop, clothing, books) into the sidebar text area, one per line

Provide Shipment Info: Fill in Shipment ID, Origin, and Destination

Click "Analyze Cargo": The system processes images and displays results

Review Results across the tabs:

Tab	Content
📊 Overview	Risk score gauge, explanation, recommendation
🔍 Detections	All detected objects and frequency chart
⚠️ Mismatch	Items not matching the declaration
🔒 Concealment	Suspicious patterns and indicators
🚨 Anomaly	Restricted, prohibited, or suspicious items
📋 Decision	Action items and escalation guidance
📄 Full Report	Complete downloadable report
📊 Risk Score Explanation
Score Range	Level	Action
0 - 25	🟢 Minimal	Release
25 - 50	🟡 Low	Review
50 - 75	🟠 Medium	Inspect
75 - 90	🔴 High	Hold
90 - 100	🚨 Critical	Alert
📝 Logging
System logs are automatically saved to data/logs/app.log and are also visible in the terminal where you launched the app.
