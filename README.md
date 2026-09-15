# Smart Procurement Slot & Queue Management System

> **SIH 2026 --- Problem Statement 26032**\
> **Team:** VantaCore\
> **Category:** Software\
> **Project:** Smart Procurement Slot & Queue Management System

A digital platform designed to reduce farmer waiting time, vehicle
overcrowding, unplanned arrivals, and uncertainty at procurement
centres.

The system connects **farmers** with **procurement-centre
staff/purchasers** through slot booking, digital tokens, live queue
updates, capacity-aware scheduling, notifications, procurement-status
tracking, and payment-status visibility.

------------------------------------------------------------------------

## Problem

Farmers can face:

-   Long and unstructured waiting times at procurement centres
-   Overcrowding during peak harvest seasons
-   Too many vehicles arriving at the same time
-   Manual and paper-based records
-   Unplanned farmer inflow that is difficult for staff to manage
-   Vehicle congestion around centres
-   Delayed procurement/payment status information
-   Uncertainty about whether a centre still has capacity

The key idea is to move from **"arrive and wait"** to **"schedule, track
and arrive at the right time."**

------------------------------------------------------------------------

## Our Solution

The platform provides two connected interfaces:

### Farmer App

1.  Login / Sign up
2.  Register crop and quantity
3.  View nearby procurement centres
4.  Compare queue, estimated waiting time and available capacity
5.  Book a fixed time window
6.  Receive a digital token / QR code
7.  Track live queue position and estimated waiting time
8.  Receive SMS / app notifications
9.  Track procurement and payment status

### Purchaser / Procurement Centre App

1.  Secure login
2.  View live farmer queue
3.  Call the next eligible farmer
4.  Verify crop and update quantity/details
5.  Update procurement status
6.  Update payment status
7.  Monitor centre capacity
8.  Manage congestion
9.  Generate daily reports and analytics

------------------------------------------------------------------------

# Core Workflow

``` text
FARMER
  │
  ▼
Login / Sign Up
  │
  ▼
Register Crop
  │
  ▼
Compare Procurement Centres
  │
  ├── Queue
  ├── Estimated Wait
  └── Available Capacity
  │
  ▼
Book Time Window
  │
  ▼
Digital Token / QR
  │
  ▼
Live Queue Tracking
  │
  ▼
Arrival at Procurement Centre
  │
  ▼
Token Verification
  │
  ▼
Crop Verification
  │
  ▼
Quality Check
  │
  ▼
Weighing
  │
  ▼
Procurement Recorded
  │
  ▼
Payment Processing
  │
  ▼
Payment Status / Completion
```

> **Important:** The application does not replace physical crop
> verification or the authorised procurement process. It digitises and
> manages the farmer's journey before, during and after the visit.

------------------------------------------------------------------------

# Queue & Capacity Management

Queue management is the core of the system.

### Fixed time windows

Instead of giving every farmer an exact minute, the system uses a **time
window**, for example:

``` text
09:00 – 09:30
09:30 – 10:00
10:00 – 10:30
```

A farmer arriving early can wait in the designated waiting area, but an
early arrival does **not automatically jump the assigned queue**.

### Dynamic queue

The centre dashboard can show:

``` text
Currently Processing : A104
Next Recommended     : A105
Farmers Waiting      : 11
Estimated Wait       : 1h 20m
```

The authorised centre staff confirms the next farmer.

### Capacity-aware booking

The system considers both:

-   Number of available slots
-   Expected crop quantity / centre capacity

If the centre becomes full, new farmers can be offered:

-   Another available time window
-   A later date
-   A nearby centre with available capacity

### Vehicle congestion control

Farmer arrival and vehicle movement can be managed separately.

``` text
Booked Slot
    ↓
Arrival Window
    ↓
Wait / Vehicle Queue
    ↓
Call Notification
    ↓
Enter Processing Area
```

This reduces the chance of every booked farmer bringing a vehicle to the
centre at exactly the same time.

------------------------------------------------------------------------

# Smart Features

### AI/ML Demand & Waiting-Time Prediction

The AI/ML service can use historical operational data such as:

-   Farmers ahead in the queue
-   Crop quantity
-   Historical processing time
-   Centre workload
-   Time of day
-   Previous centre performance

The prototype can start with a rules-based ETA and later replace it with
a trained prediction model.

### Smart Centre Recommendation

Farmers can compare centres using:

``` text
Centre A
Queue: 12
Estimated wait: 1.5 hr
Load: Medium

Centre B
Queue: 8
Estimated wait: 1 hr
Load: Low
```

The system can recommend the centre with the most suitable combination
of **queue, capacity and waiting time**.

------------------------------------------------------------------------

# Notifications

Notifications can be sent through:

-   Firebase push notifications
-   SMS
-   WhatsApp
-   Email

Example:

> Your token A105 is approaching. Please be ready to proceed to the
> procurement area.

For feature-phone or low-literacy users, **SMS / IVR / voice-based
support** can provide an alternative to a smartphone-only workflow.

------------------------------------------------------------------------

# Prototype

## Farmer & Purchaser / Centre Staff Flow


The prototype shows the two sides of the system:

-   Farmer mobile interface
-   Purchaser / centre-staff interface
-   Farmer login flow
-   Slot and queue management
-   Crop verification
-   Procurement status
-   Payment update
-   Reports

------------------------------------------------------------------------

## Technical Architecture


### Frontend

-   **React.js** --- Web application
-   **Flutter** --- Cross-platform mobile application

### Backend

-   **Node.js** --- REST API and business logic
-   **Socket.io** --- Real-time queue/status updates
-   **Python** --- AI/ML services

### Database

-   **MongoDB** --- user, farmer, purchaser, slot, queue, procurement
    and transaction data

### Notifications & Communication

-   **Firebase** --- push notifications
-   **Twilio** --- SMS and WhatsApp
-   **AWS SNS / SMTP** --- email notifications

### AWS Infrastructure

-   **EC2** --- application/server hosting
-   **S3** --- file and document storage
-   **SQS** --- background jobs and queue management
-   **Secrets Manager** --- credentials and secrets
-   **KMS** --- encryption/key management

------------------------------------------------------------------------

# 🔐 Security & Access Control

The planned system uses role-based access:

``` text
Farmer
  │
  ├── Register crop
  ├── Book slot
  ├── View token
  ├── Track queue
  └── View procurement/payment status


Centre Staff / Purchaser
  │
  ├── Manage queue
  ├── Verify crop
  ├── Update procurement
  ├── Update payment status
  └── View reports


Admin
  │
  ├── Monitor centres
  ├── View analytics
  ├── Monitor capacity
  └── Manage system configuration
```

Security features planned for implementation include:

-   Authentication
-   OTP verification
-   Role-based access control
-   Input validation
-   Secure API communication
-   Encrypted sensitive data
-   Secrets management
-   Audit logs

------------------------------------------------------------------------

# 📊 Feasibility & Viability


### Feasibility

-   Uses existing smartphone/SMS penetration
-   Works with current procurement-centre infrastructure
-   Cloud-based architecture supports phased scaling
-   Can be piloted at a small number of centres
-   Supports multilingual and low-connectivity scenarios

### Main Challenges

-   Low digital literacy
-   Inconsistent rural internet connectivity
-   Staff resistance to changing manual processes
-   Data accuracy during initial registration
-   Coordinating real-time information across multiple centres

### Mitigation

-   SMS/IVR and voice support
-   Offline-first approach
-   Simple multilingual UI
-   Staff training
-   Phased pilot rollout
-   Feedback-driven improvements

------------------------------------------------------------------------

# 🌱 Expected Impact

### For Farmers

-   Less unnecessary travel
-   Reduced waiting time
-   Better visibility of queue position
-   Better planning of vehicle arrival
-   Transparent procurement and payment status

### For Procurement Centres

-   Better control over daily inflow
-   Reduced overcrowding
-   Digital farmer records
-   Better capacity planning
-   Real-time queue visibility
-   Less manual coordination

### For Government / Administration

-   Better operational visibility
-   Digital procurement records
-   Centre-wise analytics
-   Identification of overloaded centres
-   Data-driven planning

------------------------------------------------------------------------

# References & Research Basis


The project research includes government platforms, parliamentary
material, procurement reports, news reports and academic/industry
research.

### Key references

1.  **e-NAM --- National Agriculture Market**\
    Ministry of Agriculture & Farmers Welfare's pan-India electronic
    trading platform.\
    https://www.enam.gov.in/

2.  **Parliamentary material on e-NAM**\
    Used to understand implementation challenges such as infrastructure,
    training and awareness.\
    https://eparlib.nic.in/bitstream/123456789/684468/1/37134.pdf

3.  **News reporting on mandi delays**\
    Used to validate real-world waiting and capacity problems.\
    https://www.freepressjournal.in/amp/bhopal/over-8-lakh-farmers-are-still-waiting-to-sell-wheat-across-madhya-pradesh

4.  **Food Corporation of India (FCI)**\
    Procurement and operational information.\
    https://fci.gov.in/

5.  **Ministry of Consumer Affairs, Food & Public Distribution**\
    Official ministry and policy context.\
    https://consumeraffairs.nic.in/

6.  **Academic / Industry Research**\
    Smart agriculture, IoT, supply-chain and AI-based demand/queue
    prediction research can support future prediction modules.

------------------------------------------------------------------------

# 🚀 Future Scope

-   ML-based waiting-time prediction
-   Demand forecasting for procurement centres
-   Automatic congestion alerts
-   Regional-language voice assistant
-   IVR booking for feature phones
-   Offline-first mobile application
-   QR-based arrival verification
-   Advanced government analytics
-   Multi-centre load balancing
-   Integration with authorised government procurement systems where
    APIs/data-sharing permissions are available

------------------------------------------------------------------------

# 🧪 Prototype Demo Flow

A strong hackathon demo can follow this sequence:

``` text
1. Farmer logs in
        ↓
2. Registers Wheat – 50 Quintals
        ↓
3. Compares nearby centres
        ↓
4. Selects centre based on queue + capacity
        ↓
5. Books 10:00–10:30 slot
        ↓
6. Receives Token A105
        ↓
7. Tracks live queue
        ↓
8. Centre staff calls A105
        ↓
9. Farmer arrives
        ↓
10. Staff verifies crop
        ↓
11. Quality check + weighing
        ↓
12. Procurement recorded
        ↓
13. Payment status updated
        ↓
14. Farmer receives notification
```

------------------------------------------------------------------------

# Why Our Approach Is Different

We are not building only a slot-booking application.

> **We manage the complete procurement journey --- from registration and
> scheduling to queue management, physical verification, procurement and
> payment-status tracking.**

The core principle is:

**Predict → Schedule → Control → Process → Track**

------------------------------------------------------------------------

# 👥 Team

**VantaCore**\
Smart India Hackathon 2026\
Problem Statement: **26032**

------------------------------------------------------------------------

## 📌 Project Status

**Prototype / Hackathon Development**

The architecture and features described above represent the proposed
system. Government-system integrations, live procurement/payment
integrations and production-scale deployment would require the
appropriate official APIs, permissions and operational approvals.