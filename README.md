# 🚨 SENTINEL-X

### Context-Aware Edge-AI Surveillance & Digital Trust Platform

**SENTINEL-X** is an Edge-AI based surveillance platform designed for **real-time crime, intrusion, and suspicious-activity detection** in smart cities and border-security environments.

Instead of treating every AI detection as an isolated alert, SENTINEL-X combines **object detection, tracking, event generation, contextual analysis, threat scoring, incident management, evidence capture, and cryptographic integrity verification** into a unified security pipeline.

---

## 🎯 What SENTINEL-X Does

```text
Camera / Video Input
        ↓
AI Object Detection
        ↓
Object Tracking
        ↓
Event Generation
        ↓
Context Analysis
        ↓
Threat Scoring
        ↓
Incident Detection
        ↓
Evidence Capture
        ↓
SHA-256 Integrity
        ↓
Local Database
        ↓
Security Report
```

The system can operate with a **real camera/video source** or with **mock camera and detector components** for development and demonstrations.

---

## ✨ Key Features

* 🤖 AI-based object detection
* 🎯 Persistent object tracking
* 🧠 Context-aware event analysis
* ⚠️ Dynamic threat scoring
* 🚨 Automated incident generation
* 📸 Evidence capture
* 🔐 SHA-256 evidence integrity verification
* 💾 Offline-first local processing
* 🗄️ Local database storage
* 📄 Automated PDF incident reports
* 🔑 Role-based access and authentication
* 🌐 Real-time WebSocket communication
* 📡 RTSP / ONVIF camera integration architecture
* 🏙️ Smart-city and border-security use cases

---

# 🧠 Core Innovation

Traditional surveillance systems often work like:

```text
Object Detected → Alert
```

SENTINEL-X instead works as:

```text
Multiple Detections
       ↓
Multiple Events
       ↓
Contextual Relationships
       ↓
Threat Score
       ↓
Unified Incident
       ↓
Evidence + Report
```

For example:

```text
Person detected
      +
Vehicle detected
      +
Restricted-zone activity
      +
Suspicious movement
      ↓
Contextual Threat Analysis
      ↓
HIGH / CRITICAL Threat
      ↓
Incident Created
```

This approach allows the system to consider **context and relationships between events**, rather than generating disconnected alerts.

---

# 🏗️ System Architecture

```text
                    ┌─────────────────────┐
                    │ Camera / Video Feed │
                    │   RTSP / ONVIF      │
                    └──────────┬──────────┘
                               ↓
                    ┌─────────────────────┐
                    │ Video Processing    │
                    │ OpenCV / GStreamer  │
                    └──────────┬──────────┘
                               ↓
                    ┌─────────────────────┐
                    │ AI Detection        │
                    │ YOLO / CV Models    │
                    └──────────┬──────────┘
                               ↓
                    ┌─────────────────────┐
                    │ Object Tracking     │
                    │ ByteTrack /         │
                    │ DeepSORT             │
                    └──────────┬──────────┘
                               ↓
                    ┌─────────────────────┐
                    │ Event Engine        │
                    └──────────┬──────────┘
                               ↓
                    ┌─────────────────────┐
                    │ Context Engine      │
                    │       CTIE          │
                    └──────────┬──────────┘
                               ↓
                    ┌─────────────────────┐
                    │ Threat Scoring      │
                    └──────────┬──────────┘
                               ↓
                    ┌─────────────────────┐
                    │ Incident Engine     │
                    └──────────┬──────────┘
                               ↓
              ┌────────────────┴────────────────┐
              ↓                                 ↓
     ┌─────────────────┐              ┌─────────────────┐
     │ Evidence        │              │ Alert /         │
     │ Capture         │              │ Notification    │
     └────────┬────────┘              └─────────────────┘
              ↓
     ┌─────────────────┐
     │ SHA-256         │
     │ Integrity Hash  │
     └────────┬────────┘
              ↓
     ┌─────────────────┐
     │ Local SQLite DB │
     └────────┬────────┘
              ↓
     ┌─────────────────┐
     │ PDF Report      │
     └─────────────────┘
```

---

# 🔄 End-to-End Working

### 1. Video Input

The system receives surveillance data from:

* IP cameras
* RTSP streams
* ONVIF cameras
* Video files
* Mock camera sources for demonstrations

### 2. AI Detection

The detection layer identifies security-relevant objects such as:

```text
Person
Vehicle
Abandoned Object
```

The architecture supports modern computer-vision models such as YOLO.

### 3. Object Tracking

Detected objects are assigned persistent tracking IDs.

Example:

```text
Person → Track ID: 17
Vehicle → Track ID: 24
```

This allows the system to understand how objects move across multiple frames instead of treating every frame as a new detection.

### 4. Event Generation

The tracking information is converted into meaningful security events.

Example:

```text
PERSON_ENTERED_ZONE
VEHICLE_DETECTED
OBJECT_ABANDONED
SUSPICIOUS_MOVEMENT
```

### 5. Context Analysis

The Contextual Threat Intelligence Engine (**CTIE**) combines related events and contextual information.

Instead of:

```text
Person detected
```

the system can reason about:

```text
Person
+
Restricted Zone
+
Time
+
Movement Pattern
+
Previous Events
```

### 6. Threat Scoring

The system calculates a threat level based on the available contextual events.

Example:

```text
Threat Score: 82
Severity: HIGH
```

Possible severity levels:

```text
LOW
MEDIUM
HIGH
CRITICAL
```

### 7. Incident Creation

When an event reaches the configured threshold, the Incident Engine creates a security incident.

Example:

```text
Incident ID : INC-001
Severity    : HIGH
Type        : Restricted Zone Intrusion
Status      : OPEN
```

### 8. Evidence Capture

Relevant information is preserved as incident evidence.

Example:

```text
Incident
Detection data
Track information
Timestamp
Threat score
Event information
Evidence metadata
```

### 9. SHA-256 Integrity

The evidence is hashed using SHA-256.

```text
Evidence
   ↓
SHA-256
   ↓
Integrity Hash
   ↓
Database
```

The hash can later be used to detect whether the stored evidence has been modified.

### 10. Database Storage

The system stores incident and event information in the local SQLite database.

Example:

```text
storage/
└── sentinel_edge.db
```

### 11. Automated Report

For high-severity incidents, the system can generate a PDF report containing incident information and evidence metadata.

```text
storage/
└── reports/
    └── incident_report.pdf
```

---

# 🧪 Demo Mode

SENTINEL-X includes mock components so the complete pipeline can be demonstrated **without connecting a physical surveillance camera**.

### Mock Camera

The mock camera simulates the video-input layer.

```text
Mock Camera
     ↓
Simulated Frames / Input
     ↓
Detection Pipeline
```

### Mock Detector

The mock detector simulates AI detections.

For example:

```text
Person detected
Vehicle detected
Abandoned object detected
```

This allows developers to test the **complete backend chain** without requiring an actual YOLO model or camera during development.

> In a production deployment, the mock components can be replaced with real camera feeds and trained AI detection models.

---

# 🧪 Full Chain Demo

The project includes an end-to-end demonstration covering the complete pipeline:

```text
Phase 1 → Video / Camera Input
Phase 2 → Detection
Phase 3 → Tracking
Phase 4 → Event Generation
Phase 5 → Context Analysis
Phase 6 → Threat Scoring
Phase 7 → Incident Engine
Phase 8 → Evidence Capture
Phase 9 → SHA-256 Integrity
Phase 10 → Local Database
Phase 11 → PDF Report
```

Run the complete demo from the project root:

```bash
python -m backend.demo_full_chain
```

---

# 📊 Sample Output

A successful demonstration can produce output similar to:

```text
========================================================
              SENTINEL-X FULL CHAIN DEMO
========================================================

[1] Camera Input
    ✓ Mock camera initialized

[2] Detection
    ✓ Person detected
    ✓ Vehicle detected

[3] Tracking
    ✓ Track ID assigned: 17

[4] Event Engine
    ✓ Security event generated

[5] Context Engine
    ✓ Context analyzed

[6] Threat Analysis
    ✓ Threat Score: 82
    ✓ Severity: HIGH

[7] Incident Engine
    ✓ Incident created
    ✓ Incident ID: INC-001

[8] Evidence Capture
    ✓ Evidence captured

[9] Integrity
    ✓ SHA-256 hash generated

[10] Database
    ✓ Incident stored in SQLite

[11] Report
    ✓ PDF report generated

========================================================
              DEMO COMPLETED SUCCESSFULLY
========================================================
```

*The exact console output, IDs, timestamps, and threat scores may vary depending on the demo configuration.*

---

# 📁 Generated Files

After running the demo, important artifacts are stored under the `storage/` directory.

```text
storage/
│
├── sentinel_edge.db
│
├── evidence/
│   └── *.json.enc
│
└── reports/
    └── *.pdf
```

### `sentinel_edge.db`

SQLite database containing local security events, incidents, and related records.

### `evidence/`

Stores captured incident evidence and metadata.

### `reports/`

Contains automatically generated PDF reports for applicable incidents.

---

# 🌐 Backend API

SENTINEL-X provides a backend service for interacting with the platform.

Example:

```bash
python -m uvicorn sentinel_x.main:app --reload --port 8000
```

The backend provides real-time communication channels including:

```text
/ws/owner
/ws/police
/ws/cyber
/ws/admin
```

These channels are intended for role-specific real-time security updates.

---

# 🔐 Security

SENTINEL-X includes several security mechanisms:

* Authentication
* Authorization
* Role-based access
* SHA-256 evidence integrity
* Local evidence storage
* Secure incident records
* Offline-first processing

The cryptographic integrity layer is designed to help detect unauthorized changes to stored evidence.

---

# 🛠️ Technology Stack

| Layer           | Technologies                     |
| --------------- | -------------------------------- |
| Language        | Python                           |
| Computer Vision | OpenCV                           |
| AI Detection    | YOLO                             |
| Tracking        | ByteTrack / DeepSORT             |
| OCR             | PaddleOCR                        |
| Video           | RTSP, ONVIF, GStreamer           |
| Backend         | FastAPI                          |
| Communication   | REST API, WebSockets             |
| Database        | SQLite + Central DB Architecture |
| Security        | SHA-256                          |
| Reports         | PDF Generation                   |
| Testing         | Mock Camera / Mock Detector      |

---

# 🏙️ Use Cases

## Smart Border Surveillance

Monitor restricted areas and identify potentially suspicious movement, unauthorized entry, vehicles, and abandoned objects.

## Smart-City Surveillance

Analyze security events in public environments and correlate multiple detections into contextual incidents.

## Digital Evidence Management

Securely preserve incident information and verify evidence integrity using cryptographic hashing.

---

# 📌 Project Status

🚧 **Prototype / Hackathon Project**

The current implementation demonstrates the complete end-to-end surveillance intelligence pipeline using both real-system architecture and mock components for testing.

Future development can include:

* Real-time IP camera deployment
* Advanced behavior recognition
* Multi-camera tracking
* Distributed edge nodes
* Centralized command center
* More AI models
* Advanced incident correlation
* Cloud/central database synchronization

---

# 👨‍💻 Project Vision

SENTINEL-X aims to transform surveillance from simple **"detect and alert"** systems into **context-aware security intelligence platforms**.

```text
DETECT
   ↓
TRACK
   ↓
UNDERSTAND
   ↓
SCORE
   ↓
RESPOND
   ↓
PRESERVE
   ↓
VERIFY
```

### SENTINEL-X

**Context-Aware Edge AI for Smarter, Secure, and Trustworthy Surveillance.**


# ⚙️ Setup & Installation

## 1. Clone the Repository

```bash
git clone https://github.com/<your-username>/sentinel-x.git
cd sentinel-x
```

## 2. Create a Virtual Environment

### Windows

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

If PowerShell blocks script execution:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Then activate again:

```powershell
.venv\Scripts\Activate.ps1
```

### Linux / macOS

```bash
python3 -m venv .venv
source .venv/bin/activate
```

---

## 3. Install Dependencies

From the **project root directory**:

```bash
pip install --upgrade pip
pip install -r backend/requirements.txt
```

If the project contains a separate edge requirements file:

```bash
pip install -r backend/requirements.txt -r edge/requirements.txt
```

---

# 🚀 Running SENTINEL-X

## Option 1 — Run the Full Chain Demo

The easiest way to verify that the complete SENTINEL-X pipeline works is to run the demonstration.

From the project root:

```bash
python -m backend.demo_full_chain
```

The demo simulates the camera and AI detection layers when no physical camera or video file is available.

The pipeline is:

```text
Mock Camera
     ↓
Detection
     ↓
Tracking
     ↓
Event Generation
     ↓
Context Analysis
     ↓
Threat Scoring
     ↓
Incident Engine
     ↓
Evidence Capture
     ↓
SHA-256 Integrity
     ↓
SQLite Database
     ↓
PDF Report
```

---

# 🌐 Running the Backend

From the **project root**:

```bash
python -m uvicorn sentinel_x.main:app --host 127.0.0.1 --port 8000 --reload
```

After the server starts, open:

```text
http://127.0.0.1:8000
```

The backend exposes WebSocket channels for different system roles:

```text
/ws/owner
/ws/police
/ws/cyber
/ws/admin
```

---

# 🎥 Using a Real Camera

SENTINEL-X can be extended to work with a real IP/edge camera.

Typical architecture:

```text
IP Camera
    ↓
RTSP / ONVIF
    ↓
GStreamer / OpenCV
    ↓
YOLO Detection
    ↓
Object Tracking
    ↓
SENTINEL-X Pipeline
```

For a camera supporting RTSP, the stream URL can be supplied to the camera-processing component according to its configuration.

Example format:

```text
rtsp://<camera-ip>:<port>/<stream>
```

> Replace the placeholder with the RTSP URL provided by your camera.

---

# 🧪 Running Without a Camera

A physical camera is **not required for the included demonstration**.

SENTINEL-X uses mock components to demonstrate the complete processing pipeline.

```text
Mock Camera
     ↓
Mock Detector
     ↓
Mock Tracking
     ↓
Events
     ↓
Threat Analysis
     ↓
Incident
     ↓
Evidence
     ↓
Report
```

This makes it possible to demonstrate the architecture during development or a hackathon without requiring live surveillance hardware.

---

# 📂 Output After Running the Demo

The demo generates local artifacts under:

```text
storage/
├── sentinel_edge.db
├── evidence/
│   └── *.json.enc
└── reports/
    └── *.pdf
```

### SQLite Database

```text
storage/sentinel_edge.db
```

Stores local security events and incident information.

### Evidence

```text
storage/evidence/
```

Contains generated incident evidence and associated metadata.

### Reports

```text
storage/reports/
```

Contains automatically generated PDF reports for applicable high-severity incidents.

---

# 🔍 Quick Verification

After installation, run:

```bash
python -m backend.demo_full_chain
```

A successful execution should progress through:

```text
Camera/Input
     ✓
Detection
     ✓
Tracking
     ✓
Events
     ✓
Context
     ✓
Threat Score
     ✓
Incident
     ✓
Evidence
     ✓
SHA-256
     ✓
Database
     ✓
PDF Report
     ✓
```

Then check:

```text
storage/
```

for the generated database, evidence, and report files.

---

# 🐛 Troubleshooting

### `ModuleNotFoundError`

Make sure the virtual environment is activated:

```powershell
.venv\Scripts\Activate.ps1
```

Then reinstall dependencies:

```bash
pip install -r backend/requirements.txt
```

### `Could not import module`

Run commands from the **project root**, not from inside the `backend` directory.

Correct:

```text
sentinel-x/
├── backend/
├── edge/
└── ...
```

Then:

```bash
python -m backend.demo_full_chain
```

### Port 8000 already in use

Run the backend on another port:

```bash
python -m uvicorn sentinel_x.main:app --host 127.0.0.1 --port 8001 --reload
```

Then open:

```text
http://127.0.0.1:8001
```

---

# 🏁 Quick Start

For users who just want to test the project:

```bash
git clone https://github.com/<your-username>/sentinel-x.git
cd sentinel-x

python -m venv .venv
.venv\Scripts\Activate.ps1

pip install -r backend/requirements.txt

python -m backend.demo_full_chain
```

To start the backend:

```bash
python -m uvicorn sentinel_x.main:app --host 127.0.0.1 --port 8000 --reload
```

**No physical camera is required for the full-chain demonstration.**
