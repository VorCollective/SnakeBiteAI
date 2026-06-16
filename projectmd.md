
# SnakeBite AI

## Comprehensive Product Requirements Document (PRD), Technical Design, and Implementation Roadmap

**Version:** 1.0
**Project Type:** AI-Powered Emergency Health Platform
**Domain:** Snakebite Surveillance, Emergency Response, Clinical Decision Support, Geospatial Intelligence
**Target Regions:** Rural and Semi-Urban Communities in Africa, Asia, and Latin America
**Initial Focus:** Kenya

---

# Executive Summary

SnakeBite AI is an integrated emergency-response ecosystem that combines artificial intelligence, geospatial analytics, computer vision, public-health surveillance, and healthcare logistics to reduce mortality and disability caused by snake envenomation.

The platform provides:

* Real-time snakebite incident reporting
* Bite-mark image analysis
* Symptom-based severity assessment
* Snake species probability estimation
* Emergency treatment routing
* Antivenom inventory visibility
* Ambulance coordination
* Risk hotspot mapping
* Predictive outbreak intelligence
* Government and healthcare dashboards

The system is designed around a core principle:

> The fastest path to effective treatment is more important than identifying the snake species.

---

# Background

According to global health organizations, snakebite envenoming remains one of the most neglected tropical health emergencies.

Challenges include:

* Delayed access to treatment
* Limited antivenom availability
* Poor incident reporting
* Weak surveillance systems
* Long travel distances
* Inadequate emergency transportation
* Limited specialist knowledge in rural facilities

Many deaths occur not because treatment does not exist, but because victims cannot reach the correct facility in time.

SnakeBite AI addresses this gap through intelligent emergency triage and healthcare routing.

---

# Vision

Create a nationwide and eventually continental snakebite intelligence network that:

* Detects incidents in real time
* Directs victims to appropriate care
* Supports clinicians
* Assists emergency responders
* Enables public-health planning
* Predicts future risk areas

---

# Strategic Goals

## Clinical Goals

* Reduce mortality
* Reduce disability
* Reduce time-to-antivenom
* Improve treatment decisions

## Operational Goals

* Improve emergency dispatch
* Improve hospital preparedness
* Optimize antivenom distribution

## Public Health Goals

* Build national snakebite surveillance
* Identify hotspots
* Improve prevention efforts

---

# Stakeholders

## Primary Users

### Victims

Individuals bitten by snakes.

### Caregivers

Family members assisting victims.

### Community Health Workers

First-line responders in remote areas.

### Ambulance Services

Emergency transport providers.

### Clinicians

Doctors and nurses treating snakebite patients.

---

## Secondary Users

### County Governments

Healthcare planning and emergency management.

### National Ministries of Health

Policy and resource allocation.

### NGOs

Snakebite prevention and treatment programs.

### Researchers

Epidemiology and ecological studies.

---

# Functional Architecture

```text
Patient
  │
  ▼
Reporting System
  │
  ▼
AI Assessment Layer
  │
  ├── Severity Engine
  ├── Bite-Mark Engine
  ├── Species Engine
  └── Risk Engine
  │
  ▼
Decision Engine
  │
  ├── Routing
  ├── Facility Matching
  ├── Ambulance Dispatch
  └── Treatment Recommendation
  │
  ▼
Emergency Response Network
```

---

# Core Modules

## Module 1: Incident Capture System

### Purpose

Capture snakebite incidents as quickly as possible.

### Input Channels

#### Mobile Application

Android and iOS.

#### USSD

For users without smartphones.

Example:

```text
*123#
1. Report Snake Bite
2. Find Treatment Center
3. Emergency Help
```

#### SMS

Example:

```text
BITE SWELLING BREATHING_PROBLEM
```

#### WhatsApp Bot

Natural language reporting.

#### Emergency Call Center Dashboard

Manual incident entry.

---

# Data Collection Schema

```json
{
  "incident_id": "UUID",
  "patient_age": 35,
  "patient_gender": "male",
  "latitude": -1.390,
  "longitude": 36.760,
  "time_of_bite": "2026-06-16T18:00:00",
  "body_location": "right_leg",
  "symptoms": [],
  "bite_images": [],
  "snake_images": [],
  "vital_signs": {}
}
```

---

# Module 2: Bite-Mark Intelligence Engine

## Objective

Analyze bite photographs and track progression.

---

## Computer Vision Tasks

### Bite Detection

Identify:

* Fang punctures
* Bite boundaries
* Multiple strike points

---

### Measurement Extraction

Calculate:

* Fang spacing
* Bite depth estimation
* Swelling area
* Swelling progression
* Tissue necrosis indicators
* Hemorrhage indicators

---

### Time-Series Analysis

Track wound progression.

Example:

```text
Image 1:
Swelling 5 cm

Image 2:
Swelling 8 cm

Progression:
+60%
```

---

# Module 3: Clinical Severity Engine

## Severity Classification

### Level 0

Dry bite suspected.

### Level 1

Mild envenomation.

### Level 2

Moderate envenomation.

### Level 3

Severe envenomation.

### Level 4

Critical condition.

---

## Features Used

### Local Symptoms

* Pain
* Swelling
* Bruising
* Blistering

### Neurological Symptoms

* Drooping eyelids
* Speech difficulty
* Paralysis

### Respiratory Symptoms

* Difficulty breathing
* Oxygen saturation decline

### Cardiovascular Symptoms

* Shock
* Hypotension

### Bleeding Indicators

* Gum bleeding
* Urine blood
* Internal bleeding signs

---

# Severity Scoring Formula

```text
Severity Score =
Respiratory × 30
+ Neurological × 25
+ Bleeding × 20
+ Swelling × 10
+ Time Delay × 10
+ Bite Progression × 5
```

Range:

```text
0–25   Low
26–50  Moderate
51–75  Severe
76–100 Critical
```

---

# Module 4: Snake Species Intelligence

## Inputs

### Geographic Data

Location of incident.

### Habitat Data

Vegetation and terrain.

### Seasonality

Rainfall patterns.

### Bite Mark Data

Extracted measurements.

### Snake Image

If available.

---

## Outputs

```json
{
  "species_probability": {
    "Puff Adder": 0.65,
    "Black Mamba": 0.10,
    "Spitting Cobra": 0.20,
    "Unknown": 0.05
  }
}
```

---

# Module 5: Facility Intelligence Network

## Healthcare Facility Registry

Track every participating facility.

---

### Stored Data

```json
{
  "facility_id": "123",
  "name": "County Referral Hospital",
  "coordinates": {},
  "antivenom_stock": 40,
  "icu_beds": 8,
  "ambulances": 4,
  "emergency_department": true
}
```

---

## Dynamic Information

### Real-Time Updates

* Antivenom inventory
* ICU occupancy
* Ambulance status
* Emergency capacity

---

# Module 6: Routing Intelligence Engine

## Goal

Find the fastest path to effective treatment.

---

## Routing Factors

### Distance

### Road Quality

### Traffic

### Flooding

### Ambulance Availability

### Facility Capability

### Severity

---

## Decision Logic

Example:

```text
Clinic A
5 km
No antivenom

Hospital B
12 km
Antivenom available

Recommendation:
Hospital B
```

---

# Module 7: Emergency Dispatch System

## Ambulance Coordination

Automatically:

* Alert nearest ambulance
* Share GPS coordinates
* Share severity score

---

## Hospital Alerting

Notify receiving facility.

Includes:

* ETA
* Severity level
* Suspected envenomation type
* Antivenom recommendation

---

# Module 8: National Snakebite Mapping Platform

## Incident Layer

Real-time incidents.

---

## Severity Layer

Color-coded:

🟢 Low

🟡 Moderate

🟠 Severe

🔴 Critical

---

## Species Layer

Probable species distribution.

---

## Antivenom Layer

Facility inventory visibility.

---

## Ambulance Layer

Live fleet locations.

---

# Module 9: Predictive Snakebite Risk Engine

## Data Sources

### Environmental

* Rainfall
* Temperature
* Humidity

### Ecological

* Vegetation
* Water sources
* Livestock density

### Historical

* Incident records

---

## Predictions

### Daily Risk

### Weekly Risk

### Seasonal Risk

---

## Outputs

```text
Kajiado County

Current Risk:
High

Expected Increase:
15%

Reason:
Recent rainfall and increased livestock movement
```

---

# Machine Learning Architecture

## Model A

### Bite Detection

Model:

* YOLOv11

Purpose:

* Detect punctures
* Detect swelling

---

## Model B

### Severity Prediction

Model:

* XGBoost
* LightGBM

Purpose:

* Clinical triage

---

## Model C

### Species Classification

Model:

* Vision Transformer

Purpose:

* Snake identification

---

## Model D

### Risk Forecasting

Model:

* Temporal Fusion Transformer

Purpose:

* Predict hotspots

---

# Data Architecture

## Database

### PostgreSQL

Transactional data.

### PostGIS

Spatial analytics.

### Redis

Caching.

### Object Storage

Images and documents.

---

# Security Requirements

## Authentication

* OAuth2
* Multi-factor authentication

---

## Encryption

* AES-256 at rest
* TLS in transit

---

## Compliance

* Kenya Data Protection Act
* HIPAA-inspired controls
* GDPR-compatible architecture

---

# API Architecture

## Incident API

```http
POST /api/incidents
```

## Severity API

```http
POST /api/severity
```

## Facility API

```http
GET /api/facilities
```

## Routing API

```http
POST /api/route
```

## Dashboard API

```http
GET /api/analytics
```

---

# Key Performance Indicators (KPIs)

## Clinical

* Mortality reduction %
* Disability reduction %

## Operational

* Average response time
* Average travel time

## AI

* Severity prediction accuracy
* Bite detection accuracy
* Routing effectiveness

## Public Health

* Coverage rate
* Incident reporting rate
* Hotspot prediction accuracy

---

# Phased Roadmap

## Phase 1 — MVP (3–6 Months)

* Mobile reporting
* GPS mapping
* Severity engine
* Facility recommendation
* Dashboard

---

## Phase 2 — Operational Deployment (6–12 Months)

* Bite-mark AI
* Antivenom tracking
* Ambulance integration
* SMS/USSD support

---

## Phase 3 — National Scale (12–24 Months)

* Predictive analytics
* Species intelligence
* Government integration
* Regional surveillance

---

## Phase 4 — Advanced Emergency Ecosystem (24+ Months)

* Drone antivenom delivery
* Satellite environmental monitoring
* Cross-border surveillance
* National emergency command center

---

# Expected Impact

The completed SnakeBite AI platform will function as:

* An emergency triage system
* A clinical decision-support platform
* A national snakebite surveillance network
* An antivenom logistics platform
* A public-health intelligence system

Its primary outcome is simple: **reduce the time between a snakebite and effective treatment, thereby saving lives and reducing long-term disability.**
