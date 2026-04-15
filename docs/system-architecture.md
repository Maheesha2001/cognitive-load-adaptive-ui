***System Architecture***

[1. Architecture Overview
[2](#architecture-overview)](#architecture-overview)

[High-Level Flow: [3](#high-level-flow)](#high-level-flow)

[2. System Components [3](#system-components)](#system-components)

[2.1 Frontend (UI Layer) [3](#frontend-ui-layer)](#frontend-ui-layer)

[Responsibilities: [3](#responsibilities)](#responsibilities)

[Technologies (example):
[3](#technologies-example)](#technologies-example)

[2.2 Tracking Layer (Browser Extension / Script)
[3](#tracking-layer-browser-extension)](#tracking-layer-browser-extension)

[• Tracked Signals: [3](#tracked-signals)](#tracked-signals)

[• Additional Signals (Recommended Upgrade ⭐):
[4](#additional-signals-recommended-upgrade)](#additional-signals-recommended-upgrade)

[• Responsibilities: [4](#responsibilities-1)](#responsibilities-1)

[2.3 Cognitive Load Engine
[4](#cognitive-load-engine)](#cognitive-load-engine)

[Approach: [4](#approach)](#approach)

[Scoring Formula: [4](#scoring-formula)](#scoring-formula)

[Load Classification: [4](#load-classification)](#load-classification)

[Responsibilities: [5](#responsibilities-2)](#responsibilities-2)

[2.4 UI Adapter (Adaptive Interface Engine)
[5](#ui-adapter-adaptive-interface-engine)](#ui-adapter-adaptive-interface-engine)

[Adaptation Rules: [5](#adaptation-rules)](#adaptation-rules)

[🔹 Low Load [5](#low-load)](#low-load)

[🔹 Medium Load [5](#medium-load)](#medium-load)

[🔹 High Load [5](#high-load)](#high-load)

[Responsibilities: [6](#responsibilities-3)](#responsibilities-3)

[3. Data Flow [6](#data-flow)](#data-flow)

[4. Technology Stack (Suggested)
[6](#technology-stack-suggested)](#technology-stack-suggested)

[5. Scalability Considerations
[6](#scalability-considerations)](#scalability-considerations)

[6. Performance Considerations
[6](#performance-considerations)](#performance-considerations)

[7. Security & Privacy Considerations
[6](#security-privacy-considerations)](#security-privacy-considerations)

[8. Future Enhancements [6](#future-enhancements)](#future-enhancements)

## **1. Architecture Overview** {#architecture-overview .unnumbered}

The system follows a **layered architecture** that captures user
behavior, processes it to estimate cognitive load, and dynamically
adapts the user interface in real time.

The system is designed as a modular, real-time adaptive interface that
operates entirely on the client side for the MVP version.

### **High-Level Flow:** {#high-level-flow .unnumbered}

**User → Frontend UI → Tracking Layer → Cognitive Load Engine → UI
Adapter → Updated UI**

## **2. System Components** {#system-components .unnumbered}

### **2.1 Frontend (UI Layer)** {#frontend-ui-layer .unnumbered}

A simulated **e-commerce product page (Daraz-like interface)** where all
user interactions occur.

#### **Responsibilities:** {#responsibilities .unnumbered}

-   Display product information (images, price, description)

-   Provide interactive elements:

    -   Add to cart

    -   Product selection

    -   Filters & sorting

-   Capture user interaction events (clicks, scrolls, navigation)

#### **Technologies (example):** {#technologies-example .unnumbered}

-   HTML, CSS, JavaScript

-   React / Angular (optional)

### **2.2 Tracking Layer (Browser Extension)** {#tracking-layer-browser-extension .unnumbered}

-   A lightweight tracking module that monitors user interaction
    behavior in real time.

#### **Tracked Signals:**

-   **Click Delay** → Time taken before clicking an element

-   **Scroll Speed** → Fast/slow scrolling patterns

-   **Number of Interactions** → Click frequency

-   **Hesitation Time** → Idle time before action

#### **Additional Signals (Recommended Upgrade ⭐):**

-   Backtracking (revisiting pages)

-   Repeated clicks (confusion indicator)

#### **Responsibilities:** {#responsibilities-1 .unnumbered}

-   Collect behavioral data

-   Preprocess signals

-   Send data to Cognitive Load Engine

### **2.3 Cognitive Load Engine** {#cognitive-load-engine .unnumbered}

The core logic unit that estimates the user\'s cognitive load level.

#### **Approach:** {#approach .unnumbered}

Rule-based scoring system (MVP-friendly)

#### **Scoring Formula:** {#scoring-formula .unnumbered}

Cognitive Load Score =

(Click Delay × 2)

\+ (Hesitation Time × 2)

\+ (Backtracking × 3)

\+ (Error Actions × 5)

\+ (Scroll Irregularity × 1)

#### **Load Classification:** {#load-classification .unnumbered}

-   **Low Load** → Smooth interaction

-   **Medium Load** → Slight hesitation

-   **High Load** → Confusion / overload

#### **Responsibilities:** {#responsibilities-2 .unnumbered}

-   Aggregate behavioral signals

-   Compute cognitive load score

-   Classify user state

-   Send output to UI Adapter

> Changes UI based on load:

-   simplify layout

-   reduce items

-   add hints

### **2.4 UI Adapter (Adaptive Interface Engine)** {#ui-adapter-adaptive-interface-engine .unnumbered}

Dynamically modifies the interface based on detected cognitive load.

#### **Adaptation Rules:** {#adaptation-rules .unnumbered}

##### **🔹 Low Load** {#low-load .unnumbered}

-   Show full interface

-   Enable all features

##### **🔹 Medium Load** {#medium-load .unnumbered}

-   Highlight important elements

-   Reduce visual clutter slightly

-   Provide subtle hints

##### **🔹 High Load** {#high-load .unnumbered}

-   Simplify layout

-   Reduce number of visible items

-   Emphasize key actions (e.g., "Buy Now")

-   Show guidance (tooltips / suggestions)

#### **Responsibilities:** {#responsibilities-3 .unnumbered}

-   Receive load classification

-   Apply UI transformation rules

-   Update UI in real time

## **3. Data Flow** {#data-flow .unnumbered}

1.  User interacts with the **Frontend UI**

2.  **Tracking Layer** captures behavioral signals

3.  Data is sent to the **Cognitive Load Engine**

4.  Engine calculates load score and classification

5.  Result is sent to the **UI Adapter**

6.  UI is dynamically updated

7.  User experiences adapted interface

## **4. Technology Stack (Suggested)** {#technology-stack-suggested .unnumbered}

  -----------------------------------------------------------------------
  **Layer**                           **Technology**
  ----------------------------------- -----------------------------------
  Frontend                            HTML, CSS, JavaScript / React

  Tracking                            JavaScript (Event Listeners)

  Backend                             Not required for MVP

  Data Handling                       JSON

  Hosting                             Localhost / AWS (optional)
  -----------------------------------------------------------------------

## **5. Scalability Considerations** {#scalability-considerations .unnumbered}

-   Modular architecture (each component independent)

-   Can replace rule-based engine with ML model later

-   Cloud integration possible (AWS, Firebase)

-   Event streaming for real-time processing

## **6. Performance Considerations** {#performance-considerations .unnumbered}

-   Lightweight tracking (avoid slowing UI)

-   Fast rule-based computation

-   Minimal DOM manipulation for UI updates

## **7. Security & Privacy Considerations** {#security-privacy-considerations .unnumbered}

-   Do not collect sensitive user data

-   Anonymize interaction data

-   Ensure transparency in tracking

## **8. Future Enhancements** {#future-enhancements .unnumbered}

-   Machine Learning-based cognitive load detection

-   Personalization using user history

-   Cross-platform support (mobile apps)

-   Real-time analytics dashboard

-   Integration with real e-commerce platforms
