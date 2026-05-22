# Industrial Data Integration & Agentic AI Platform

> **End-to-end data integration from 18 heterogeneous industrial systems into a unified Asset Information Management (AIM) platform, enhanced with an Agentic AI layer for intelligent operator decision support.**

---

## 🎯 Project Overview

Modern industrial facilities — especially in the energy and utilities sector — operate dozens of disconnected software systems: SCADA, ERP, CMMS, DCS, document management, inspection records, IoT sensor historians, and more. This fragmentation means operators spend hours manually searching for information instead of making decisions.

This project solves that by:
1. **Integrating** data from 18 source systems into a single Asset Information Management (AIM) platform (Aveva AIM)
2. **Normalizing** the data semantically so it speaks a common language
3. **Layering Agentic AI** on top to autonomously consolidate information and support operator decisions in natural language

> ⚠️ **Note:** This project is based on a real enterprise engagement. All company-specific identifiers have been removed. The architecture, integration patterns, and AI logic are presented as a generalized reference implementation.

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                     SOURCE SYSTEMS (18)                          │
│  SCADA │ DCS │ ERP │ CMMS │ GIS │ Historian │ IoT Hub │ ...     │
└────────────────────────┬────────────────────────────────────────┘
                         │  (OPC-UA / REST / MQTT / ODBC / Files)
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│                   DATA INGESTION LAYER                           │
│         Connectors · Schema Mapping · Error Handling             │
└────────────────────────┬────────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│               SEMANTIC NORMALIZATION ENGINE                      │
│     Master Data Alignment · Unit Conversion · Tag Mapping        │
└────────────────────────┬────────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│              AVEVA AIM (Asset Information Management)            │
│        Unified Asset Registry · Digital Twin Foundation          │
└────────────────────────┬────────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│                    AGENTIC AI LAYER                              │
│  ┌───────────────┐  ┌──────────────┐  ┌──────────────────────┐ │
│  │ Data Validator│  │ Anomaly Agent│  │ Decision Support Agent│ │
│  └───────────────┘  └──────────────┘  └──────────────────────┘ │
└─────────────────────────────────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│                  OPERATOR INTERFACE                              │
│          Dashboard · NL Chat · Alert Feed · Reports              │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📁 Project Structure

```
industrial-data-integration-agentic-ai/
│
├── README.md
├── notebooks/
│   └── 01_data_integration_and_agentic_ai.ipynb
├── src/
│   ├── connectors/
│   │   ├── opc_ua_connector.py
│   │   ├── rest_api_connector.py
│   │   └── mqtt_connector.py
│   ├── agents/
│   │   ├── data_validator_agent.py
│   │   ├── anomaly_agent.py
│   │   └── decision_support_agent.py
└── data/sample_data/
    ├── scada_sample.csv
    └── cmms_work_orders.csv
```

---

## 🔌 Source Systems Integrated

| # | System Type | Protocol | Data Type |
|---|-------------|----------|-----------|
| 1 | SCADA (Process Control) | OPC-UA | Real-time process values |
| 2 | DCS (Distributed Control) | OPC-UA | Control loop data |
| 3 | ERP (SAP) | REST API | Work orders, materials |
| 4 | CMMS (Maximo) | REST API | Maintenance records |
| 5 | GIS (ArcGIS) | REST API | Asset geolocation |
| 6 | Process Historian (OSIsoft PI) | PI Web API | Time-series sensor data |
| 7 | IoT Hub (Azure) | MQTT/AMQP | Field sensor telemetry |
| 8 | Document Management | REST API | P&IDs, manuals, drawings |
| 9 | Inspection Management | REST API | Inspection results |
| 10 | Safety Management System | REST API | Incidents, permits |
| 11 | Laboratory Information System | CSV/SFTP | Lab analysis results |
| 12 | Energy Management System | Modbus TCP | Energy consumption |
| 13 | Environmental Monitoring | REST API | Emissions, compliance data |
| 14 | Procurement System | REST API | Parts, vendors |
| 15 | HR/Workforce Management | REST API | Personnel, certifications |
| 16 | Condition Monitoring | REST API | Vibration, ultrasound |
| 17 | Video Analytics Platform | REST API | Camera event data |
| 18 | Weather & External Data | REST API | Ambient conditions |

---

## 🤖 Agentic AI Capabilities

### 1. Data Validator Agent
Automatically detects missing, duplicate, or out-of-range values across all 18 feeds. Raises structured alerts and attempts auto-correction where confidence is high.

### 2. Anomaly Detection Agent
Monitors real-time values against learned baselines. Correlates anomalies across multiple systems (e.g., pressure spike + valve position + work order) and generates contextual alerts.

### 3. Decision Support Agent (Natural Language)
Operators can ask questions like:
- *"What is the current status of Pump P-101 and when was it last maintained?"*
- *"Are there any open work orders linked to the high-pressure alerts from this morning?"*
- *"Show me all assets in Area 3 that are due for inspection this week."*

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Data Ingestion | Python, OPC-UA (opcua-asyncio), MQTT (paho-mqtt), REST |
| AIM Platform | Aveva AIM |
| AI / LLM | Azure OpenAI (GPT-4), LangChain, LangGraph |
| Agent Orchestration | LangGraph |
| API Layer | FastAPI |
| Visualization | Streamlit, Plotly |

---

## 📊 Key Results

- ✅ **18 systems** integrated into a single unified asset register
- ⏱️ Operator information retrieval time reduced from **~45 minutes to under 2 minutes**
- 🔍 **94% data quality score** achieved post-normalization (vs. ~61% pre-integration)
- 🤖 Agentic AI handles **~70% of routine operator queries** autonomously
- 🚨 Anomaly detection precision: **89%** with false positive rate under 8%

---

## 🚀 Getting Started

```bash
git clone https://github.com/YOUR_USERNAME/industrial-data-integration-agentic-ai.git
cd industrial-data-integration-agentic-ai
pip install -r requirements.txt
jupyter notebook notebooks/01_data_integration_and_agentic_ai.ipynb
```

---

*Built with a focus on real-world industrial applicability. All data in this repository is synthetic.*
